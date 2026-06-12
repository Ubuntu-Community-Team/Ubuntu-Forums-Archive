---
title: "BBC iPlayer wont work with Lucid - why ?"
date: 2010-05-01
forum: General Help
---

### Post by Scunnered on 2010-05-01
I initially downloaded Lucid as a 32 bit RC and loaded it on an old desktop to see what it looked like.  As it worked a treat I downloaded the AMD64 bit final release and downloaded this to my laptop.

In each instance I loaded the restricted extras and also checked that adobe flash was loaded as flash was a problem with the BBC iPlayer before.

I can listen to the iPlayer on the 32 bit RC but not on the 64 bit final. Can anyone offer guidance on this.

PS.  Trying the 32 bit RC on the laptop I was able to listen OK.

---

### Post by BrokeMahPC on 2010-05-01
Not much experience with 64bit but my guess would be you need to ensure that you have the 64bit codecs and plugins - check synaptic.
For example - 
32bit should download w32codecs
64bit should download w64codecs
check if the flash plugin has different versions.

edit - yes there is a 64bit flash plugin!

---

### Post by Untitled_No4 on 2010-05-01
I'm running 64 bit and iplayer works fine here, but I installed the 64 bit Flash plugin which in my experience works better with 64 bit OS.

---

### Post by Scunnered on 2010-05-02
Many thanks to you both for your reply.

I went to synaptic and when entering adobe flash am offered two flashplugin.
The one marked - installer is downloaded. The other - non free has not been.
Should I be loading the non free or can you offer better guidance as I am struggling here.

---

### Post by zaphod777 on 2010-05-02
for x64 I found this is the best way to get the x64 flash 

[http://astoryworthtelling.wordpress.com/2009/12/11/flash-broke-again/](http://astoryworthtelling.wordpress.com/2009/12/11/flash-broke-again/)

---

### Post by Scunnered on 2010-05-02
**zaphod777**

Many thanks for your reply.  Unlike you I have not yet mastered the Hitchhikers Guide am am still in "***panic***" mode when ever anyone suggests that I download anything other than a package via Snyaptic.

I am still at the stage in Linux that I am in my comfort zone when working within the confines of Ubuntu.

In the circumstances I will wait and see if anyone can guide me to where I may find the solution within Synaptic.

Again thanks

---

### Post by crossy on 2010-05-02
> **Scunnered said:**
> **zaphod777**

Many thanks for your reply.  Unlike you I have not yet mastered the Hitchhikers Guide am am still in "***panic***" mode when ever anyone suggests that I download anything other than a package via Snyaptic.

I am still at the stage in Linux that I am in my comfort zone when working within the confines of Ubuntu.

In the circumstances I will wait and see if anyone can guide me to where I may find the solution within Synaptic.

Again thanks

I'm going to be rebuilding my laptop - which seems to have similar specs to yours - either today or tomorrow, so once I've done so I'll post the update process needed back here. I need it for work on Monday, so fingers crossed for a trouble free install (doing a fresh install rather than a migrate).

That said, I've also had "issues" in the past with Firefox+Flash+iPlayer (this on 8.04LTS-x64) and switching to Opera seemed to work better. Just a shame that the Beeb weren't forward thinking enough to allow software like "get_iplayer" which is just superb - I got a version of this before the lawyers were loosed and use it for grabbing the 6Music content I want.

Bob :KS

---

### Post by zaphod777 on 2010-05-02
No problemo. 

I believe you might be out of luck though because the flash version in Synaptic is the x32 version which can have problems. 

Then one linked to in the blog I posted is directly from the Adobe site and is their x64 beta flash version. 

I always had problems with the version that is in synaptic. 

You might try installing the dev version of the google chrome browser as it has flash built in.

---

### Post by Untitled_No4 on 2010-05-02
The easiest and safest way to install Flash 64 bit on Ubuntu is to use the ppa.

1. Remove your current flash install if you have it:
```
sudo aptitude remove flashplugin-installer
```

2. Add the [ppa]("https://launchpad.net/~sevenmachines/+archive/flash") to your sources list. There are several ways to do it so choose your favourite, but to use command line do this:
```
sudo add-apt-repository ppa:sevenmachines/flash
```

3. Update apt and install Flash 64 bit:
```
sudo aptitude update
sudo aptitude install flashplugin64-installer
```

4. Restart firefox

---

### Post by Scunnered on 2010-05-02
My sincere thanks to everyone for their assistance. 

I am pleased to say that by following the information provided by **Untitled_No4** normal service has been resumed.

Initially the server did not supply the confirmation key from Ubuntu but repeating the process obtained the key and everything from there went smoothly.

Having addressed my major concern I can now keep an eye on the forum and see if the small niggles that I have are being addressed.

Again thanks very much

---

### Post by DanlG on 2010-06-11
I tried all the solutions I could find. No luck.  In desperation I tried Chrome browser, then Epiphany.  Finally found happiness with Epiphany.  Now listening to BBC! :-)

---

### Post by momist on 2010-09-27
Thanks for your help with this Untitled_No4 - it worked for me too!

---

