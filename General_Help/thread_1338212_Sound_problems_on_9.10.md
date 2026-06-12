---
title: "Sound problems on 9.10"
date: 2009-11-26
forum: General Help
---

### Post by ibrahim.k on 2009-11-26
Hi,
I have installed ubuntu 9.10 i can hear sounds but when i play mp3 song i can see that there is no mp3 codecs and after pressing on search to install the proper codecs I get this message

E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

    

I have installed it on my hp-dv6 1045 and when i plug in my headphones the sound keeps coming from the speakers !! why ?


Many thanks

---

### Post by ene_dene on 2009-11-26
For codecs it's best way to install ubuntu-restricted-extras packet from medibuntu repository.
You can add medibuntu repository by running this command:
```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
```
After that install the package ubuntu-restricted-extras from synaptic package manager or in command line write:
```
sudo aptitude install ubuntu-restricted-extras
```
And you will have sound and every other music/video codec.

As for headphones... hmm I'm not sure how is that connected to Ubuntu, are you 100% sure that you connected to right jack, and not in mic for example?

---

### Post by ibrahim.k on 2009-11-26
> **ene_dene said:**
> 

As for headphones... hmm I'm not sure how is that connected to Ubuntu, are you 100% sure that you connected to right jack, and not in mic for example?


I am using the right jacks I only have one for headphones and been using it with windows.

According to the mp3 and restricted format thing I dont think i understand what you mean because i am new on ubuntu can you pleas explain this to me


Thank you very much

---

### Post by ene_dene on 2009-11-26
> **ibrahim.k said:**
> I am using the right jacks I only have one for headphones and been using it with windows.
I don't know then, you'll need to play with audio settings.
> 
According to the mp3 and restricted format thing I dont think i understand what you mean because i am new on ubuntu can you pleas explain this to me


Thank you very much

In Windows when you wanted to install something you clicked on .exe file and program would install.
In Linux/Ubuntu most of the software is located in repositories of software. However not all the repositories come by default.
One of these repositories is named Medibuntu ([http://medibuntu.org](http://medibuntu.org)). That repository has everything you need for multimedia. And the easiest way is to install "ubuntu-restricted-extras" package which contains all the codecs.
First line I gave to you is adding the Medibuntu repository to list of your repositories, the second line is installing "ubuntu-restricted-extras" package.
I gave you the instructions how to do it in terminal (copied from their site), you can also do it the graphical way, but I think it's easier if you just copy paste the instructions.
Anyway if you want to do it the graphical way go to system->administration->synaptic package manager->settings->repository->other software, then click on "+add" and add the line:
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free
press ok, and update.
That line is the repository you'll be downloading from.
Than it is also good to add a key signature to confirm that you trust the source... link you'll need to find by your self.
Anyway it's much more complicated this way, just paste what I copied to you.

EDIT: oh yes, if you choose the graphical way, after update search for package "ubuntu-restricted-extras"

---

