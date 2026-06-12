---
title: "unable to correct problems you have held broken packages"
date: 2009-11-10
forum: General Help
---

### Post by Raymond Lanphere on 2009-11-10
I am new to Ubuntu, roughly two months, and recently upgraded from 9.04 to 9.10.  
For some reason my flash player, or lack there of, is not working properly on different websites.
Youtube, for example, is fine.  However,  when I go to Aion to look at 3D character models it doesn't detect my flash player.
When I was prompted to download a new one (java) I received an error message stating "unable to correct problems you have held broken packages," 
I honestly don't know where to go from here please help me.

---

### Post by mikewhatever on 2009-11-10
Hi, and welcome to the forums,

the fact that youtube works is a good start. If you want others to test something that doesn't work for you online, provide a link. I don't know what's the problem with Aion, whatever that is, but java isn't the same as flash player. You can install it from the Software Center.
...and here is how to fix broken packages:
[https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages](https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages)

---

### Post by Raymond Lanphere on 2009-11-10
Thank you for responding and I am very happy to be here.

This is a link to what I was talking about.

[http://na.aiononline.com/livestatus/character-legion/search?serverID=1&charID=137411](http://na.aiononline.com/livestatus/character-legion/search?serverID=1&charID=137411)

Furthermore, I included some screen shots of my experience and your link was, unfortunately, unhelpful.

---

### Post by michy99 on 2009-11-10
Enter the following command in a terminal and post any error message you get.```
sudo dpkg --configure -a
```

---

### Post by Raymond Lanphere on 2009-11-10
The command prompted for my password then nothing happened.
sudo dpkg --configure -a

---

### Post by michy99 on 2009-11-10
Ok, then try this:```
sudo apt-get install sun-java6-plugin
```

---

### Post by Raymond Lanphere on 2009-11-10
I would like to thank you for your efforts to help me before I begin.

I was met with this (see attachment)

---

### Post by michy99 on 2009-11-10
Post the output of```
cat /etc/apt/sources.list
```(or open the file /etc/apt/sources.list and paste the contents here.)

---

### Post by Raymond Lanphere on 2009-11-10
This is what appeared.

---

### Post by ranch hand on 2009-11-10
Not butting in here but where you can, cut and paste.  It is easier to read and take snips from, if needed, to clarify points for you.

---

### Post by Raymond Lanphere on 2009-11-10
Sorry, I'm also new to forum etiquette.

---

### Post by ranch hand on 2009-11-10
There is nothing wrong with that.  It is just that people need to be able to actually read what you post as easily as possible.

To butt in, I really think you need to check the broken packages business out.  This will come back and haunt you.

If you pull up synaptic and click on status (lower left of page) broken packages, if there are any, should be listed.

---

### Post by Raymond Lanphere on 2009-11-10
Nothing happens when I go to Synaptic Package Manager > Status > Edit > Fix Broken Packages.  So, I am utterly lost.

---

### Post by ranch hand on 2009-11-10
Did ypu just click on the "status" button on the lower left of the page?

We are not talking here of the option in the Edit menu.

Just want to know;

A>If there are broken packages

B>how many

---

### Post by mc4man on 2009-11-10
I'm terrible with firefox so can't say do this....

but I'd probably take a look at sun-java6-jre and sun-java6-bin, it certainly appears that you've retained the jaunty versions thru your upgrade to karmic

(a bit odd that jaunty has 16 in version, karmic 15

note that the sun-java-plugin is just a meta package and when viewing your web page (correctly) the plug-in in use here is adobe-flash....

---

### Post by Raymond Lanphere on 2009-11-10
> **mc4man said:**
> but I'd probably take a look at sun-java6-jre and sun-java6-bin, it certainly appears that you've retained the jaunty versions thru your upgrade to karmic
.

How would I go about taking a look at those two?

---

### Post by ranch hand on 2009-11-10
What is up on the synaptic front?

---

### Post by Raymond Lanphere on 2009-11-10
I didn't know how to answer this without a screen shot =D.

---

### Post by ranch hand on 2009-11-10
If you look at the bottom of the page, on the bottom bar, it says "0 broken".

You have run "sudo dpkg --configure -a" with no result.  This is a good thing.  "0 broken" is a good thing.

Now if you just learn to look at the Ubuntu wiki and search the forums for your answers rather than third party blogs, you will have an easier life.

Another good place for information on setting up your OS is;

[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)

Follow their instructions for getting your sources.list set up with medibuntu repo and the public key for it.

They will have you run "sudo apt-get update".  This is a good start.  Now use synaptic to download approved packages from approved repos.

ubuntu-restricted-extras will have about everything you need in the flash and java lines.

---

