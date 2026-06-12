---
title: "where to set MAN_PATH and INFO_PATH"
date: 2010-05-19
forum: General Help
---

### Post by equaeghe on 2010-05-19
Hi,


Where do I globally set/append MAN_PATH and INFO_PATH in an Ubuntu installation?


TIA,

Erik

---

### Post by dino99 on 2010-05-19
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by equaeghe on 2010-05-19
> **dino99 said:**
> mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

Sorry, but that post does not seem relevant. Am I missing something?

---

### Post by dino99 on 2010-05-19
> **equaeghe said:**
> Sorry, but that post does not seem relevant. Am I missing something?

this post is about "installation", which is what you ask for.

---

### Post by equaeghe on 2010-05-19
> **dino99 said:**
> this post is about "installation", which is what you ask for.

The word installation appears in my post, but it is not about installation.
Did you read it or was it an automated reply or some such?
Please, if you answer a post, do make sure it is on-topic: posts which already have replies (even though they are not useful or to the point) get looked at less.

---

### Post by gmargo on 2010-05-19
First off, you can set global environment variables in the /etc/environment file.

On the MANPATH (no underscore) variable, you should read the manpath(1) man page to understand the format of MANPATH, since it can either override the standard configuration or append to it, based on the format.  See also the manpath(5) man page to understand the /etc/manpath.config file.

Sorry, can't help on the INFO part.

---

### Post by stephendlynch on 2010-05-26
as said above running manpath will tell you what your current $MANPATH is if you have one, and will assemble a "good' one if not.  it does so by checking out the text file /etc/manpath.config 

so one way to add to your $MANPATH would be to edit this file.  

another TOTALLY KLUGEY way i was able to use this but also not dive into /etc/manpath.config was to just add two lines to /home/myself/.bashrc : 

MANPATH=`manpath`
MANPATH=/your/new/manpath:$MANPATH

i recommend first saving your original .bashrc file somewhere, like 
cp ~/.bashrc ~/.bashrc_orig

you could probably do something similar for INFO_PATH but i'll probably get yelled at here for this already.

---

### Post by equaeghe on 2010-05-26
Dear gmargo & stephendlynch,

Thanks for the help. I got the MANPATH fixed (man manpath was the way to go) and I stopped caring about INFOPATH. So I'm marking this solved.

---

