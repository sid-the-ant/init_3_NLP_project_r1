# Init_3 NLP Project: Round 1
Team Members:
1. Ajitesh Saxena
2. Siddhant Bhatnagar
3. Kushagra Chaturvedy

This repository contains the jupyter notebook and the corresponding .txt files used for the Data Analysis and Part of Speech tagging.


# **Problem Statement:**

1. Choose two books (given in .txt files),
2. prepare them for tokenization;
3. convert them into a set of tokens, either a set containing stop-words or not;
4. perform part of speech tagging on these tokens;
5. perform data analysis on these; and,
6. using the analytics, create a word cloud.

# **Data Description:**

The different properties of data can be accessed using the wc command from a UNIX shell or an equivalent, where -l(lines), -w(words),-m(characters) are the options used.

1. **Frankenstein:**

_As Viktor Frankenstein (Kenneth Branagh) is dying he shares a tale of gruesome terror with a sea captain. Viktor, using previous experiments by a brilliant scientist, was able to bring a creature (Robert De Niro) assembled from body parts back to life. Once he realized how destructive his experiments had become, he abandoned the creature and tried to live a normal life with his fiancé (Helena Bonham Carter). The lonely creature seeks out Viktor and demands one of two things: a bride or revenge._

**(Source: www.google.com)**

      1. lines = 7,803
      2. words=77,985
      3. characters = 439,992

1. **Moby Dick:**

_The book is the sailor Ishmael&#39;s narrative of the obsessive quest of Ahab, captain of the whaling ship Pequod, for revenge on Moby Dick, the giant white sperm whale that on the ship&#39;s previous voyage bit off Ahab&#39;s leg at the knee._

**(Source: en.wikipedia.org)**

      1. lines =4,652
      2. words=42,393
      3. characters= 240,973

# **Data Pre-processing Steps:**

In data pre-processing, we make sure that a text corpus containing words of different cases, special characters and numbers, is streamlined and only contain the words and/or numbers and characters essential to the analysis we are currently performing.

For the current analysis, the following steps were performed in the **pre\_process\_text(filename)** function:

1. We go through the lines in the file and concatenate them into a string.
2. We then replace the new line (\n) with a &#39; &#39; so that we get all the words in one line.
3. We convert the entire string to lowercase using the lower() function.
4. Using iteration and python&#39;s string.punctuation, we remove all the punctuation from the corpus.
5. Next, we get rid of the &#39;chapter no. N&#39; from the corpus using a regular expression **&quot;**** [cC]hapter [0-9]+&quot;**.
6. We remove the numbers from the corpus using the regular expression **&quot;[0-9]+&quot;**.

1. The suffixes for numbers, e.g. the &#39;st&#39; in &#39;1st&#39;, are removed using another regular expression **&quot;(^|\s)+th\s+|(^|\s)+rd\s+|(^|\s)+nd\s+|(^|\s)+st\s+&quot;**
2. Finally, we remove the special types of inverted commas and the long hyphen separately by replacing them by an empty string.

After this pre-processing, we tokenize the words using the word\_tokenize() function from the nltk.tokenizer package , the

Next, we may either remove the stop-words or not. Tokenization has been done for both cases, in the tokenify(book) and tokenify\_rem\_stop(book) functions.

The removal of the stop-words is accomplished by using stopwords.words(&#39;english&#39;), which is a function taken from the nltk.corpus package. The values returned from this function can be converted into a list, and the words in the corpus that are the stop-words are removed via iteration.

Thus, we now have two sets of tokens for each book, one with stop-words and one without. These are now ready for further data analysis and part of speech tagging.

# **Function/Library Descriptions:**

1. **NLTK:** NLTK or _Natural Language Toolkit_ is a platform for building python programs/scripts to work on human languages. In this project, we will be using the following functions from this platform:

1. **nltk.tokenize.word\_tokenize:** used to convert a string of words to a list of tokens
2. **nltk.tokenize.sent\_tokenize:** used to break the corpus into sentences, which are then used for part of speech tagging
3. **nltk.corpus.stopwords:** contains a predefined list of stop-words for different languages.
4. **ntlk.corpus.treebank:** used to implement Penn&#39;s treebank part of speech tagging.

1. **collections.Counter:** used to count hashable objects, which are tokens in this case. Basically, it counts number of each token and puts the count of each token corresponding to it in a map, i.e. a key-value pair.

1. **matplotlib.pyplot:** used to create graphs for frequency and part of speech tagging.

1. **Axes:** Add an axes to the current figure and make it the current axes.
2. **Subplot:** Add a subplot to the current figure. Used here to divide the canvas into 4 parts, for _ **rows:** _ with and without stop-words, and _ **columns:** _ frequency distribution graph and word cloud.

1. **wordcloud.WordCloud:** used to generate a word cloud.

# **Inference:**

From the frequency distribution, corresponding data analysis and the part of speech tagging, we can infer the following:

1. The frequency of each word in the corpus of each book
2. The most frequent words in the corpus after removing the stop-words.
3. The part of speech of each word in the corpus.
4. The frequency distribution of the various part of speeches in each book.
5. The significant change in frequency distribution after the removal of stop-words implies extensive use of stop-words.
