---
title: "Remove duplicate lines from a text file."
date: 2010-12-16
forum: General Help
---

### Post by webcabbie on 2010-12-16
So I have 67 text files. 

Contained within each of these 67 text files is about 1 million urls. 

Yes. I have 67 text files that contain 1 million lines of urls each. 

I am sure I am swimming in duplicates. I tried opening one text file and clicking sort ----->remove duplicates. 

Now Gedit is not responding my processor is maxed out to 100% and I think I am finally ready to delve into some command line code. 

Can anyone give me idiot proof instructions on how to sort the duplicates out of each one of these 67 text files? How about no duplicates across all 67?
Remember IDIOT PROOF!

I~m ready when you are. 

MJC

---

### Post by Soldier2580 on 2010-12-16
Okay, I'm kinda not the guy who is an ubuntu knowledge-pro, BUT, however, I am now learning the shell, so this makes an excellent exercise :D

So, here is what I think you should do (idiot proof):

-Know where your text files are, you'll need that directory
-Open a Terminal
-type in the terminal (or copy paste and fill in):
```
cat Desktop/bla1.txt Documents/bla2.txt |sort|uniq|less > Desktop/Dupefree.txt

```with Desktop/bla1.txt and Documents/bla2.txt being the directory to your text files. Here, bla1 is on my desktop, and bla2 is in Documents, in my home folder. You wanted it idiot proof, right? :)
-Close the terminal
-Now, on your desktop is a shiney new text document 'Dupefree', which should be what you want. Or I should redo my homework :/




EDIT: ok, I forgot, you have 67 txt files.. That will take a while. Fast way, easier: Try putting the text files in a folder (eg; Desktop/urlfolder)and make sure thats the only thing in there.

Then do this in the terminal:
```
cat Desktop/urlfolder/* |sort|uniq|less > Desktop/Dupefree.txt

```
That will save you a hell lot of typin :p
Let me know if it works :)

---

### Post by webcabbie on 2010-12-16
o.k. someone else claims they filtered out the dupes and has it down to around 3 million unique urls but I am going to do what you suggested just to double check. 

The sorting they did resulted in 3 text files of 1 million each. 

any idea how to break one text file into chuncks of 5,000 urls? 

The help you have givenme is much appreciated!

---

### Post by Soldier2580 on 2010-12-20
Oi!sry for the wait.. If it hasn't been fixed yet, here's a simple way to do it is:

```
split -l5000 Desktop/Dupefree.txt Desktop/urlpart
```

*NOTE: it is 'split -l5000' its a small L, not a number one*



That divides the Dupefree textfile into new parts, named urlpartaa, urlpartab, urlpartac etc. :)

---

### Post by webcabbie on 2011-04-06
I am trying to do this again and I keep getting the reply invalid argument. Any ideas?

---

### Post by webcabbie on 2011-04-06
I figured it out sorry.. I had the folder in another folder.. my bad!

---

### Post by webcabbie on 2011-05-05
Hey bro is there a way to run this command so the files come out 1,2,3, instead of lettered?



EDIT: ok, I forgot, you have 67 txt files.. That will take a while. Fast way, easier: Try putting the text files in a folder (eg; Desktop/urlfolder)and make sure thats the only thing in there.

Then do this in the terminal:
```
cat Desktop/urlfolder/* |sort|uniq|less > Desktop/Dupefree.txt

```
That will save you a hell lot of typin :p
Let me know if it works :)[/QUOTE]

---

### Post by Soldier2580 on 2011-06-16
Hey there, still need help on this matter? I almost forgot about this post when, believe it or not, I just had to clean up 8 files of each about 1million lines of text, too :D 

So if you like, I could take a look if i can find a way to a numbered solution?

S

---

