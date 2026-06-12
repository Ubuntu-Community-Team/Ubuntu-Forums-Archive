---
title: "Youtube video stream cannot start"
date: 2009-12-04
forum: General Help
---

### Post by ronux on 2009-12-04
Hello,

I am unable to stream a particular set of YouTube videos. Generally speaking I have no problem in streaming any type of video. 
I am running Karmic, I tried on Firefox and Opera. It does work on Windows instead :-?. So my guess is that there is a OS / browser issue or maybe some settings on my machine. 
The page where the videos are hosted is political. If for whatever reason it is offensive to you, please disregard this post:
[http://kucinich.us/index.php?option=com_content&task=view&id=2847&Itemid=2#MSNBC]("http://kucinich.us/index.php?option=com_content&task=view&id=2847&Itemid=2#MSNBC")

If you try streaming one or more of these videos let me know if it works or not and if there is a solution to this problem.

Many thanks.

R.

---

### Post by lyall on 2009-12-04
ronux


have to installed Medibuntn?
You will need to install.  Go to [http://www.medibuntu.org/]("http://www.medibuntu.org/")

or 
for the terminal enter

sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update

Youtube videos will work after you have installed the w32codecs

please see the medibuntu site for more info and details for your PC/Laptop

I have no problem with Firefox or Opera see the viewing from your post

Good Luck and have for learning

---

### Post by ronux on 2009-12-04
@lyall: I thought I had all the Medibuntu packages installed. As I said I never had any issue with streaming beside the web page that I posted. Thanks for the code. It did work!

R.

---

