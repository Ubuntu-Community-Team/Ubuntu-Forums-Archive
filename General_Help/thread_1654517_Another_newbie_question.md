---
title: "Another newbie question"
date: 2010-12-28
forum: General Help
---

### Post by CP2 on 2010-12-28
So, I will soon begin building my computer and enter the world of Linux. My question is since linux is supposed to be highly customizable, then how easy/hard would it be to get some of the different features of different linux distros into one made-for-me OS? 

I haven't dealt with a lot of linux distros, so I don't even know where to start on what I would do if I could do it. I like music production and streaming multimedia. There are also other features I would like to get, but I don't know what I would get yet.

So again, how simple would it be to custome tailor Ubuntu to my specifications? Or would I be better of finding a different distro that I like?

And I always hear folks talk about different types of Ubuntu or something. Like fiesty, lucid, maverick, etc. What does all that mean? Differences?

---

### Post by howefield on 2010-12-28
> **CP2 said:**
> I like music production and streaming multimedia. There are also other features I would like to get, but I don't know what I would get yet.

So again, how simple would it be to custome tailor Ubuntu to my specifications? Or would I be better of finding a different distro that I like?

Sounds like Ubuntu Studio would be a good bet for you, have a look at ...

[http://ubuntustudio.org/](http://ubuntustudio.org/)

> And I always hear folks talk about different types of Ubuntu or something. Like fiesty, lucid, maverick, etc. What does all that mean? Differences?

Each Ubuntu release has a code name during the development stage,  prior to full release when they will usually be referred to by the release number, eg, 10.04, 10.10 - the numbers refer to the year and month of release.

Your main choice would be either Lucid or Maverick, in that Lucid (10.4.1) is the current Long Term Support option and Maverick (10.10) is the current non Long Term Support release.

---

### Post by CP2 on 2010-12-28
> **howefield said:**
> Sounds like Ubuntu Studio would be a good bet for you, have a look at ...

[http://ubuntustudio.org/](http://ubuntustudio.org/)



Each Ubuntu release has a code name during the development stage,  prior to full release when they will usually be referred to by the release number, eg, 10.04, 10.10 - the numbers refer to the year and month of release.

Your main choice would be either Lucid or Maverick, in that Lucid (10.4.1) is the current Long Term Support option and Maverick (10.10) is the current non Long Term Support release.

Ok now the codename thing makes sense. Are those usually stable? Are they made to be more stable than it's so called predecessor? Like 10.4.1 > 10.4 ???

---

### Post by corncob on 2010-12-28
Ubuntu Ultimate has many extra applications already installed:
[http://distrowatch.com/table.php?distribution=ultimate](http://distrowatch.com/table.php?distribution=ultimate)

Although I don't use it either, I thought OpenArtist was pretty cool:
[http://openartisthq.org/](http://openartisthq.org/)

---

### Post by K.J. on 2010-12-28
You can always pick and choose features as you like. You can start with a pretty vanilla maverick install and then add repositories for software that isn't in the default.

For example, I use my eeepc 901 as a soft synth for my midi keyboard. I started with lUbuntu, then added the UbuntuStudio repositories to get the real-time kernel and a few other things.

---

### Post by CP2 on 2010-12-28
> **K.J. said:**
> You can always pick and choose features as you like. You can start with a pretty vanilla maverick install and then add repositories for software that isn't in the default.

For example, I use my eeepc 901 as a soft synth for my midi keyboard. I started with lUbuntu, then added the UbuntuStudio repositories to get the real-time kernel and a few other things.

That sounds pretty cool. I'm new to the Linux thing, so I am not sure what EXACTLY you mean by repositories. Like a storage space for software packages? And what is this real time kernel you speak of? I'm KINDA familiar with what a kernel is, but could you possibly elaborate? I'm also going to wiki it, so you don't need to answer if you don't want to.

---

### Post by K.J. on 2010-12-28
Repositories are essentially what you described. They are central places that house software pre-compiled for your version of Linux. They are simple to add to apt, and since 9.10 (correct me if I'm wrong), you don't even need to worry about what version you are using or adding keys anymore. You simply add the repository in synaptic (the package manager) and then update. The software in the repository will be added to the list.

The real-time kernel is a version of the linux kernel tweaked with a higher I/O clock. Essentially, it means I/O, like a midi instrument, will have a lower latency. Generally, when playing live you want your total latency to be around or under 10 ms, or else there will be a noticeable delay and may throw rhythm off.

---

### Post by CP2 on 2010-12-28
> **K.J. said:**
> Repositories are essentially what you described. They are central places that house software pre-compiled for your version of Linux. They are simple to add to apt, and since 9.10 (correct me if I'm wrong), you don't even need to worry about what version you are using or adding keys anymore. You simply add the repository in synaptic (the package manager) and then update. The software in the repository will be added to the list.

The real-time kernel is a version of the linux kernel tweaked with a higher I/O clock. Essentially, it means I/O, like a midi instrument, will have a lower latency. Generally, when playing live you want your total latency to be around or under 10 ms, or else there will be a noticeable delay and may throw rhythm off.

Alrighty then cool. thanks for the info man. Much appreciated.

---

