---
title: "Firefox profile start"
date: 2009-10-03
forum: General Help
---

### Post by Robbyx on 2009-10-03
What is the best way to use firefox to access just one web address?

Pending a better solution  I have created a new profile with the specific home page. How do I run FF from the command line so that it starts in that profile?

---

### Post by akakingess on 2009-10-03
Try starting firefox from the terminal with the command " firefox -p " without the quotation marks. This will start it up to create a new profile, but also should bring up the profile manager, there you should be able to select the default profile, or to ask you every time you star firefox.

---

### Post by Robbyx on 2009-10-03
Is there a way of just quoting the profile  I wish to use in the command line?

---

### Post by akakingess on 2009-10-03
There probably is, but I am at work and not able to test it out, you could try firefox -p --help or whatever will list the options, or just try some out, if you know the name of the profile, I would try firefox -p--profilename and see if that does it. Sorry, if I were in front of one of my many Ubuntu machines at home I would have a definite answer, unfortunately I am stuck at work ;(

---

### Post by Robbyx on 2009-10-03
According to the help:

Mozilla options
	
	-P <profile>		Start with <profile>.

I can not get it to work. It loads my default what ever  I do:

rob@rob-desktop:~$ firefox -P Harmony
rob@rob-desktop:~$ firefox -ProfileManager

To get to the profile manager I had to install an extension called Profile manager and synchronizer, to run from within FF!

I seem to remember there is a program that runs a javascript page in FF as if it were a  standalone program. Do you know what it is called?

---

### Post by akakingess on 2009-10-03
Are you talking about [firebug]("https://addons.mozilla.org/en-US/firefox/addon/1843") ? See if that is what you are looking for, sorry for all of the trouble, but I have never had a problem like that with the profile manager;)

---

### Post by Robbyx on 2009-10-03
> **akakingess said:**
> Are you talking about [firebug]("https://addons.mozilla.org/en-US/firefox/addon/1843") ? See if that is what you are looking for, sorry for all of the trouble, but I have never had a problem like that with the profile manager;)

I am not referring to firebug it was something much less technical. I used it about a year ago to run google translate as if it was a stand alone program. I clicked on an icon, and although firefox was run in order to bring up translate it did not look like the normal firefox. I was as if I was running translate on my desktop.

---

### Post by akakingess on 2009-10-03
Grease Monkey, or Web Developer would be the only other 2 that I know of that you might be talking about. Sorry, I haven't been there (mozilla.org) in so long, the number of add-ons has gone up x1,000...

---

### Post by lovinglinux on 2009-10-03
If Firefox is already opened, then use this:

```
firefox -P -no-remote "profilename"
```

> **Robbyx said:**
> I am not referring to firebug it was something much less technical. I used it about a year ago to run google translate as if it was a stand alone program. I clicked on an icon, and although firefox was run in order to bring up translate it did not look like the normal firefox. I was as if I was running translate on my desktop.

It's Mozilla Prism. Click [here](apt:prism) to install it.



.

---

### Post by Robbyx on 2009-10-03
For some reason prism would not work. It just loaded the normal FF. Instead I have done:

firefox -P -no-remote "profilename"

This worked.

Thanks for the advice. I was looking for prism but as you can see, can not use it.

---

