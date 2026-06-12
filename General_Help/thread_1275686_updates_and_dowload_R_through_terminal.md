---
title: "updates and dowload R through terminal?"
date: 2009-09-26
forum: General Help
---

### Post by awayguy on 2009-09-26
Halo

well one of my proplems is the following:

i use ubuntu eee, and i cant make the updates. theres always an error.
how can i make it through the terminal?

my other question, in want install R
im typing: sudo agt-get R , but nothing happens.

this is madness! XD

with regards

---

### Post by wojox on 2009-09-26
I don't know what R is but try:

```
sudo apt-get update && sudo apt-get install R
```

---

### Post by Cato2 on 2009-09-26
"R" is not a valid package in Ubuntu 8.04 at least.  Also the command (if this was a valid package) would be ```
sudo apt-get install r
``` - if you have trouble with apt-get you can just use Synaptic of course.

A quick google for "r package ubuntu" found [http://edtechdev.blogspot.com/2007/08/getting-r-set-up-in-ubuntu.html](http://edtechdev.blogspot.com/2007/08/getting-r-set-up-in-ubuntu.html) which may be what you want - there's a link at the top for 8.10 instructions.

---

### Post by tommcd on 2009-09-26
> **awayguy said:**
> 
i use ubuntu eee, and i cant make the updates. theres always an error.
how can i make it through the terminal?

To get the updates for Ubuntu from the terminal:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
Or you could just use update manager.
If you are still getting errors then post your /etc/apt/sources.list file here.

---

### Post by awayguy on 2009-09-26
well, first problemm solved.

but after starting the R instalation the reply is:

E: Couldn't find package R

---

### Post by tommcd on 2009-09-26
> **awayguy said:**
> 
but after starting the R instalation the reply is:
E: Couldn't find package R
What is **R** ???
Can you tell us the exact name of the package you are trying to install???
You can search for the proper name of a package with:
```
aptitude search package_name
```
Replace package_name with the name of the package.  A "i" before the package means it is installed. A "p" before the package means it is not installed.

---

### Post by ddrichardson on 2009-09-26
> **tommcd said:**
> What is **R** ???
Can you tell us the exact name of the package you are trying to install???

[http://www.r-project.org/](http://www.r-project.org/)

Goodness, we can Google as well as posters can :)

Incidentally I think the package is r-base but I'll check.

---

### Post by ddrichardson on 2009-09-26
Yes it is:
```
sudo apt-get install r-base
```

---

### Post by tommcd on 2009-09-26
> **ddrichardson said:**
> [http://www.r-project.org/](http://www.r-project.org/)
Goodness, we can Google as well as posters can :)

The OP should have said that then. If someone only gives the bare minimum of info and expects someone to solve their problem then we have to ask.

---

### Post by ddrichardson on 2009-09-26
> **tommcd said:**
> The OP should have said that then. If someone only gives the bare minimum of info then we have to ask.
Not as long as we are offering support on a distribution that specifically aims at new users, the time it takes to post "what is R?" is probably higher than Googling it.:smile:

---

### Post by awayguy on 2009-09-26
sorry folks, yes i found it on the r-project.org side.
i thought first it will download it with the command: sudo apt-get install R

because on the computers at the university i just type R and the program starts.
so it was a bad thought, ive should try in the begining to check out r-project site.

i'm trying it on the eeepc. it wonders me how it will work.

thanks

---

### Post by ddrichardson on 2009-09-26
R has a lot of packages - you might need to find out what your university is using.

---

### Post by tommcd on 2009-09-26
> **ddrichardson said:**
> ... the time it takes to post "what is R?" is probably higher than Googling it.:smile:
Not really. How is anyone supposed to know what someone is referring to when the only info they give is "R"?
You got lucky with a good guess with that R-project. R could have been many things.

---

### Post by ddrichardson on 2009-09-26
> **tommcd said:**
> Not really. How is anyone supposed to know what someone is referring to when the only info they give is "R"?
You got lucky with a good guess with that R-project. R could have been many things.
No, I use R and have done for years but seeing as you're on a quest and can't take a joke...

[http://www.google.co.uk/search?rlz=1C1GGLS_en-GBGB343GB343&sourceid=chrome&ie=UTF-8&q=r](http://www.google.co.uk/search?rlz=1C1GGLS_en-GBGB343GB343&sourceid=chrome&ie=UTF-8&q=r)

Oh look - 8 out of 11 hits !!

---

### Post by tommcd on 2009-09-26
> **ddrichardson said:**
> No, I use R and have done for years... 
Exactly! So you use "R" so you knew what it was. The point is that most people who are not familiar with the R-project would have no idea what he meant with "R". I am not the ony one in this thread who was puzzled by "R".

---

### Post by ddrichardson on 2009-09-26
> **tommcd said:**
> Exactly! So you use "R" so you knew what it was. The point is that most people who are not familiar with the R-project would have no idea what he meant with "R". I am not the ony one in this thread who was puzzled by "R".
Deftly ignoring the Google link...

---

### Post by tommcd on 2009-09-26
> **ddrichardson said:**
> Deftly ignoring the Google link...
Well, thank you for explaining what "R" is. I will remeber it next time this comes up. Sorry, but I never would have thought to search for just "R".
 The next time someone asks how to install "W", "B, or "Q" or whatever, I will be more diligent and search for whatever letter of the alphabet the OP is looking for.

---

### Post by ddrichardson on 2009-09-26
> **tommcd said:**
> Well, thank you for explaining what "R" is. I will remeber it next time this comes up. Sorry, but I never would have thought to search for just "R".
 The next time someone asks how to install "W", "B, or "Q" or whatever, I will be more diligent and search for whatever letter of the alphabet the OP is looking for.
How about if you don't know what you're talking about, as is clear in this instance, you just keep quiet? You know I'm being light hearted but you want to be surly about it. No-one is going to ask about W, B or Q as they aren't software - R is and it's called R.

---

### Post by marshag63 on 2009-09-26
[http://www.stats.bris.ac.uk/R/](http://www.stats.bris.ac.uk/R/)

---

### Post by tommcd on 2009-09-26
> **ddrichardson said:**
> How about if you don't know what you're talking about, as is clear in this instance, you just keep quiet? You know I'm being light hearted but you want to be surly about it. No-one is going to ask about W, B or Q as they aren't software - R is and it's called R.
Well, you certainly don't come across as lighthearted. Gee, and I thought I was being lighthearted!
Face it dude, "R" is a rather esoteric program that would most definitely not be on the short list of programs that the great mass of the 918,256 members (as of this writing) would be asking how to install. How many people who are not familiar with R would know what someone is asking for when the only clue they give is "R"? If anything, this thread illustrates what a great resource the Ubuntu forums are, does it not?  I'm glad you knew what R was and solved this puzzle.

As for "W", "B", and "Q", these are not as far fetched as you might think. I mean, X in linux is the well known X-server, is it not? C is a well known programming language is it not? Slackware has a virtual alphabet soup of package series that one can choose to install:
[http://slackware.com/getslack/torrents.php](http://slackware.com/getslack/torrents.php)
 It turns out that there is a "W" in linux:
[http://linux.about.com/library/cmd/blcmdl1_w.htm](http://linux.about.com/library/cmd/blcmdl1_w.htm)
Type w in the terminal. It works! Who would have thought?

---

### Post by ddrichardson on 2009-09-26
> **tommcd said:**
> As for "W", "B", and "Q", these are not as far fetched as you might think. I mean, X in linux is the well known X-server, is it not? C is a well known programming language is it not? Slackware has a virtual alphabet soup of package series that one can choose to install:
[http://slackware.com/getslack/torrents.php](http://slackware.com/getslack/torrents.php)
Want to see something really crazy? It turns out that there is a "W" in linux:
[http://linux.about.com/library/cmd/blcmdl1_w.htm](http://linux.about.com/library/cmd/blcmdl1_w.htm)
Type w in the terminal. It works! Who would have thought?
As for "B", it turns out there is a B linux also:
[http://leb.net/blinux/blinux-faq.html](http://leb.net/blinux/blinux-faq.html)
And, how about this? There is also a "Q":
[http://www.q-linux.com/](http://www.q-linux.com/)
I never would have known any of this if it were not for this thread!
You mean you Googled them? :P

---

### Post by tommcd on 2009-09-26
> **ddrichardson said:**
> You mean you Googled them? :P
I sure did! Well, I use Slackware, so I knew about that.
For what it's worth, there is a B and a Q linux also:
[http://www.counterpunch.org/~blinux/](http://www.counterpunch.org/~blinux/)
[http://www.q-linux.com/](http://www.q-linux.com/)
But this is perhaps stretching things a bit.
I never would have thought to google R either. Now I know what R is.

---

### Post by Cato2 on 2009-09-27
> **awayguy said:**
> well, first problemm solved.

but after starting the R instalation the reply is:

E: Couldn't find package R

As I said in my original message (because I tested "apt-get install r" for you), **that is not the name of a valid package** - if you had read my message or simply followed the steps in the linked page it would have been clear.

---

