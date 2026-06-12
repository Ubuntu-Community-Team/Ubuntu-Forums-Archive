---
title: "Synaptic &quot;mark all upgrades&quot; doesn't work?"
date: 2012-01-09
forum: General Help
---

### Post by pretty_whistle on 2012-01-09
How do I get it to work?

I'm probably doing something wrong so lets start with how does it work?  Do you just hit the button and then hit 'apply'?

---

### Post by nnm1974 on 2012-01-09
I do most of those things using the terminal:
 
> sudo apt-get update && sudo apt-get upgrade
 
This will work. But keep in mind that you need to have synaptic closed before executing the above command. Otherwise you get an errormessage saying that some files are locked. 
 
Good luck!

---

### Post by pretty_whistle on 2012-01-09
> **nnm1974 said:**
> I do most of those things using the terminal:
 

 
This will work. But keep in mind that you need to have synaptic closed before executing the above command. Otherwise you get an errormessage saying that some files are locked. 
 
Good luck!
If I use this command won't it install all updates found automatically?  I won't get a list of them so I can choose which ones I want to install, will I?

---

### Post by Rex Bouwense on 2012-01-09
If you do use those commands recommended all of the updates will be downloaded and installed.
To pick and choose which updates to install use Update Manager.  Or if you want to use Synaptic Package Manager, I believe that you have to mark each one for installation.  Not really sure about that.

---

### Post by pretty_whistle on 2012-01-09
> **Rex Bouwense said:**
> If you do use those commands recommended all of the updates will be downloaded and installed.
To pick and choose which updates to install use Update Manager.  Or if you want to use Synaptic Package Manager, I believe that you have to mark each one for installation.  Not really sure about that.
That's what I thought.  Those commands will install whatever is found and won't let me choose.

---

### Post by Elfy on 2012-01-09
Synaptic will also mark ALL of the updates once you've told it to mark updates, you might be able to unmark specific ones - never tried myself.

---

### Post by pretty_whistle on 2012-01-09
> **forestpiskie said:**
> Synaptic will also mark ALL of the updates once you've told it to mark updates, you might be able to unmark specific ones - never tried myself.
Ok.  Then that's what I don't want to do.

This resolved the question for me, thanx.

---

