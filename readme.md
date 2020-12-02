# CMPS 530 - Final Project
For your final project you will continue analysis of movie data we've worked with throughout the semester.  While there is not necessarily a lot more code involved in the final project - the main difference are as follows:

- I am asking you to work with a library we've not discussed, and beyond some basic pointers, you will need to do your own independent research in order to work with it.
- You will need to think about whether your answers are correct - much like the real world, you aren't being provided with the answers so you can check your work!

# Part 1
Among all movies, list the top 10 genres - in terms of number of movies associated with the genre.  Do not include "no genres listed" in the most frequent list.  List the number of movies with each of the 10 genres.

# Part 2 
For each of the top 10 genres, find the 10 most common *nouns* that appear in movies associated with that genre.  For this part, you will need to use a *natural language processing* library called `nltk`.  See the tips below for guidance - but this is an area that I am expecting you to do some of your own research.

# Tips and Clarifications
None of the following are absolute requirements.  If you find other ways of making things work, and are confident in your results - there is nothing wrong with that.  Please don't try to invent your own natural language processing though... that's not wise.

## Counting
You are going to be doing a lot of frequency counting for this project.  I highly recommend you take a look at `Counter` - https://docs.python.org/3/library/collections.html#collections.Counter  it will make your life a bit easier - **but you are not required to use it**.

## Installing `nltk`
The **[Natural Language Toolkit](https://www.nltk.org/)** - `nltk` is the most commonly used library for understanding / recognizing natural languages.  The documentation for installation is found here:  https://www.nltk.org/.  

To install `nltk` with `conda`, use the following command:
```
conda install nltk
```

Natural language processing requires lots of data, and you will need to download such data - which `nltk` makes fairly easy.  From within your python script (or jupyter notebook), you simply import the library and download the *popular* data packages:

```py
import nltk

nltk.download('popular')
```

Additional documentation can be found in the online [nltk book](http://www.nltk.org/book/).

## Tokenization
For a given title, you will need to "tokenize" the title to get a list of words - see `nltk.tokenize`.  Chapter 3 in the online book linked above has some useful examples.

## Word Stemming
You are counting the frequency of nouns, you want to use a technique called *word stemming* to avoid counting the plural or other variations of the same noun as separate things.  For instance, you want to treat *dog* and *dogs* as the same thing - *dog*.

`nltk` contains word stemming - **do not do this yourself!**  I recommend using `PorterStemmer`, included in the `nltk.stem` module.  

One important note - word stemmers aren't perfect.  Do not concern yourself with the quality of the word stemming result.  For example, I tokenized and then stemmed "The quick brown fox jumps over the lazy dog".  I got back "lazi" as one of the word stems - don't worry about something like that.

## What counts as a noun?
Remember that you are only counting the frequency of **nouns**.  This should include all types of nouns (proper nouns, etc.). Take a look at `nltk.pos_tag` for this.  Note that the classifier identifies a number of types of nouns, but their labels always start with **NN**.