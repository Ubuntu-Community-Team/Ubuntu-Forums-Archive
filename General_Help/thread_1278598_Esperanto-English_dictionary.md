---
title: "Esperanto-English dictionary"
date: 2009-09-29
forum: General Help
---

### Post by Docaltmed on 2009-09-29
I've checked around in all of the gnome-dictionary servers, I can't find an Esperanto-English dictionary.

Is there one, that uses any client, or is stand-alone?

Dankon!

---

### Post by sopadeajo on 2009-09-29
I do not have any answer to your question (new to Linux) but i would take advantage of it to ask a related one. Where to find french and spanish dictionnaries for gnome-dictionary-applet 2.26.0 (situated in the panel)?

there is an option in Preferences for Spanish Dictionnaries but it does not work: lookup failed for host es.dict.org on port 2628

---

### Post by Docaltmed on 2009-09-29
> **sopadeajo said:**
> I do not have any answer to your question (new to Linux) but i would take advantage of it to ask a related one. Where to find french and spanish dictionnaries for gnome-dictionary-applet 2.26.0 (situated in the panel)?

there is an option in Preferences for Spanish Dictionnaries but it does not work: lookup failed for host es.dict.org on port 2628

Everything I know about dictionaries, I learned [here]("http://ubuntuforums.org/showthread.php?t=705408").

---

### Post by sopadeajo on 2009-09-29
> **Docaltmed said:**
> Everything I know about dictionaries, I learned [here]("http://ubuntuforums.org/showthread.php?t=705408").

Thanks for the link to the thread. I have read it and followed all the steps to install the English Spanish Freedict Dictionnary.
But the dictionnary does not work probably because the server is not the default one: dict.org or else the port is not 2628
Seems that there is no way to know the name of the server.
Hope that someone with more knowledge will help us and that you'll find your esperanto-english for gnome dictionnary.

-desktop:~$ dict -h dict.org --dbs
Databases available:
 gcide      The Collaborative International Dictionary of English v.0.48
 wn         WordNet (r) 2.0
 moby-thes  Moby Thesaurus II by Grady Ward, 1.0
 elements   Elements database 20001107
 vera       Virtual Entity of Relevant Acronyms (Version 1.9, June 2002)
 jargon     Jargon File (4.3.1, 29 Jun 2001)
 foldoc     The Free On-line Dictionary of Computing (27 SEP 03)
 easton     Easton's 1897 Bible Dictionary
 hitchcock  Hitchcock's Bible Names Dictionary (late 1800's)
 bouvier    Bouvier's Law Dictionary, Revised 6th Ed (1856)
 devils     THE DEVIL'S DICTIONARY ((C)1911 Released April 15 1993)
 world02    CIA World Factbook 2002
 gazetteer  U.S. Gazetteer (1990)
 gaz-county U.S. Gazetteer Counties (2000)
 gaz-place  U.S. Gazetteer Places (2000)
 gaz-zip    U.S. Gazetteer Zip Code Tabulation Areas (2000)
 --exit--   Stop default search here.
 afr-deu    Africaan-German Freedict dictionary
 afr-eng    Africaan-English Freedict Dictionary
 ara-eng    English-Arabic Freedict Dictionary
 cro-eng    Croatian-English Freedict Dictionary
 cze-eng    Czech-English Freedict dictionary
 dan-eng    Danish-English Freedict dictionary
 deu-eng    German-English Freedict dictionary
 deu-fra    German-French Freedict dictionary
 deu-ita    German-Italian Freedict dictionary
 deu-nld    German-Nederland Freedict dictionary
 deu-por    German-Portugese Freedict dictionary
 eng-afr    English-Africaan Freedict Dictionary
 eng-ara    English-Arabic FreeDict Dictionary
 eng-cro    English-Croatian Freedict Dictionary
 eng-cze    English-Czech fdicts/FreeDict Dictionary
 eng-deu    English-German Freedict dictionary
 eng-fra    English-French Freedict Dictionary
 eng-hin    English-Hindi Freedict Dictionary
 eng-hun    English-Hungarian Freedict Dictionary
 eng-iri    English-Irish Freedict dictionary
 eng-ita    English-Italian Freedict dictionary
 eng-lat    English-Latin Freedict dictionary
 eng-nld    English-Netherlands Freedict dictionary
 eng-por    English-Portugese Freedict dictionary
 eng-rom    English-Romanian FreeDict dictionary
 eng-rus    English-Russian Freedict dictionary
 eng-spa    English-Spanish Freedict dictionary
 eng-swa    English-Swahili xFried/FreeDict Dictionary
 eng-swe    English-Swedish Freedict dictionary
 eng-tur    English-Turkish FreeDict Dictionary
 eng-wel    English-Welsh Freedict dictionary
 fra-deu    French-German Freedict dictionary
 fra-eng    French-English Freedict dictionary
 fra-nld    French-Nederlands Freedict dictionary
 hin-eng    English-Hindi Freedict Dictionary [reverse index]
 hun-eng    Hungarian-English FreeDict Dictionary
 iri-eng    Irish-English Freedict dictionary
 ita-deu    Italian-German Freedict dictionary
 jpn-deu    Japanese-German Freedict dictionary
 kha-deu    Khasi-German FreeDict Dictionary
 lat-deu    Latin-German Freedict dictionary
 lat-eng    Latin-English Freedict dictionary
 nld-deu    Nederlands-German Freedict dictionary
 nld-eng    Nederlands-English Freedict dictionary
 nld-fra    Nederlands-French Freedict dictionary
 por-deu    Portugese-German Freedict dictionary
 por-eng    Portugese-English Freedict dictionary
 sco-deu    Scottish-German Freedict dictionary
 scr-eng    Serbo-Croat-English Freedict dictionary
 slo-eng    Slovenian-English Freedict dictionary
 spa-eng    Spanish-English Freedict dictionary
 swa-eng    Swahili-English xFried/FreeDict Dictionary
 swe-eng    Swedish-English Freedict dictionary
 tur-deu    Turkish-German Freedict dictionary
 tur-eng    Turkish-English Freedict dictionary
 english    English Monolingual Dictionaries
 trans      Translating Dictionaries
 all        All Dictionaries (English-Only and Translating)
 web1913    Webster's Revised Unabridged Dictionary (1913)
 world95    The CIA World Factbook (1995)

---

### Post by sopadeajo on 2009-09-30
Seems that nobody in this forum is interested in dictionaries nor in Esperanto.

I have downloaded stardict to use as a dictionnary (using synaptic) but i do not understand quite well how it works.It seems it comes by default with a chinese-english dictionary (the authors of the software are chinese). and that you have to download the dictionaries you want to use. I did so with the Longman english dictionary but when i wanted to situate it in the right folder: usr/share/stardict/dic access was denied and i couln't do it.
Besides, the program seems to be always listening on port 2628 and i had to kill the process several times to let it stop. Something is not quite well working with it.
Anybody knowing more than me?

---

### Post by sopadeajo on 2009-09-30
I have found a english-esperanto and esperanto-english dictionaries to use with stardict (you can download stardict using synaptic), here:
[http://stardict.sourceforge.net/Dictionaries_misc.php](http://stardict.sourceforge.net/Dictionaries_misc.php)

---

### Post by sopadeajo on 2009-10-01
I have found the way to correctly install the downloaded dictionaries to usr/share/stardict/dic.You type gksudo nautilus in Terminal. This will allow you to copy (by right clicking) the downloaded and uncompressed files and paste them in the destination folder which is protected unless you do it this way.
I have installed The Longman Dictionary of Contemporary English and the 12E English Spanish Dictionary this way.Besides i had the French Littré (installed via Synaptic) which is an old (187x) but good french to french dict and a english to chinese amusing dict. I can see all of them in the same window and regulate the order they appear. The dictionaries are working very well and very quick.
But still need to learn more things about Stardict.

Edited;
here is the page to find (in blue near the top) the dictionaries to download:

[http://stardict.sourceforge.net/Dictionaries.php](http://stardict.sourceforge.net/Dictionaries.php)

---

### Post by sopadeajo on 2009-10-02
>  Thanks for the link to the thread. I have read it and followed all the steps to install the English Spanish Freedict Dictionnary.
But the dictionnary does not work probably because the server is not the default one: dict.org or else the port is not 2628
Seems that there is no way to know the name of the server.[http://ubuntuforums.org/showthread.php?t=705408](http://ubuntuforums.org/showthread.php?t=705408)

These dictionaries must be downloaded to your computer and so are not on line dictionatries. The applet in the panel "Dictionary Lookup"-->Preferences-->Add-->whatever name you want in Description-->127.0.0.1 in hostname (with Jaunty only, i believe).

Here iare the references for downloading dictionaries for the gnome dictionary:
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=dict](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=dict)

Example: 
[B]dict-freedict-eng-spa for the english-spanish dictionary
[/B]

---

### Post by Stator Akane on 2011-03-21
I attempted to find such a dictionary for dictd, but I didn't have much luck.
I also attempted to create a new dictionary, but I was having unresolvable errors.

So I just decided just to make my own.
It's a PHP script that works via the command line (PHP installation required).
There is some setup required that is explained in the included documentation.
It works in a similar manner to dict with some of its functionality.

An example of a search:

```
> dictionary_search esperanto english word devi
devi -> have to, must, ought to, should
```The arguments are "from language", "to language", "search method", and "search term". The search methods supported are word, prefix, suffix, and substring.

Undoubtedly the syntax for a given query is long but, with a little work, one can set up something like bash aliases for easier queries.

The Esperanto-English dictionary is included, but it's possible to create additional dictionaries (see the HOWTO if interested).

While I've tried to ensure that the script works without problems and the directions are understandable, if any problems crop up, please let me know.

Download: [http://foxdentech.com/akane/download/dictionary_search_0.1.tar.bz2](http://foxdentech.com/akane/download/dictionary_search_0.1.tar.bz2)

---

