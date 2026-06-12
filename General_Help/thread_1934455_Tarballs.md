---
title: "Tarballs"
date: 2012-03-02
forum: General Help
---

### Post by NickoHall on 2012-03-02
Hi :)

I've been trying to compile .tar.gz and tar.bz2 files following on line guides and they all work for me exactly right up to the point where I have to enter ./configure. I extract the files from the tarball, i cd to the directory and follow every instruction implicitly but ./configure never works. I have installed as many package things from the get-app commands that are listed in the guides and yet whenever i type ./configure it just says unknown command. Is there something I'm missing? Help would be appreciated! 

Thanks :)

---

### Post by nothingspecial on 2012-03-02
First off, have you installed build-essential?

Next, not all source packages have configure scripts, does the one you are trying to compile have one?

---

### Post by enjoijesus94 on 2012-03-02
Compiling Is Easy But It Goes To No Offense To The Person Wanting To Know How To Do It

First Exract Your File.

Then cd it
```
cd /home/username/TarballFile
```

Depends On The Files Within It.

So Run 

```
./configure
```

Then

```
make
```

And Finally

```
sudo make install
```

Now If Its 'Sh'
Make Sure Its Executable.
By Typing Inside Terminal.
```
sudo chmod +x /home/username/folder/shscript
```

Then Run It
```
./shscripthere
```

Need Help Just Post.

---

### Post by NickoHall on 2012-03-03
I didn't realise that some were .sh instead. I have figured out that it is sh and I tried following your instructions but when I try to run it it just says Cannot execute. Am I missing something? 

Thanks for the replies :)

---

### Post by Paqman on 2012-03-03
Let's back up a step. What exactly are you trying to install? If it's available in the repos, in a PPA or as a .deb then that's the way to go before messing with tarballs.

---

### Post by NickoHall on 2012-03-03
I would have got it through those methods already if I could. I'm trying to install the latest beta Firefox 11 and I downloaded the Tarball right from the site and it contains an sh file but it says cannot execute if I try to run it and yes i did the command that is supposed to give you allowance to execute the .sh. I've googled around and I follow every instruction I find exactly to the point and even fiddle around but it just says cannot execute Everytime.

---

### Post by MG&amp;TL on 2012-03-03
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa")

;)

EDIT: only use that if you want cutting-edge. The "beta" is below.

---

### Post by Paqman on 2012-03-03
> **MG&TL said:**
> [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa")

;)

That's the daily build, which is a bit more "bleeding edge" than what the OP is after. You can get Firefox 11 from:
[https://launchpad.net/~mozillateam/+archive/firefox-next]("https://launchpad.net/~mozillateam/+archive/firefox-next")

---

### Post by NickoHall on 2012-03-03
Hi, thanks for the links, I added the ppa and got firefox-trunk from the synaptic manager but now im at a loss for what to do now. How does this allow me to get the latest beta of firefox? Sorry for being so blonde haha :P

---

### Post by Paqman on 2012-03-03
> **NickoHall said:**
> Hi, thanks for the links, I added the ppa and got firefox-trunk from the synaptic manager but now im at a loss for what to do now. How does this allow me to get the latest beta of firefox? Sorry for being so blonde haha :P

If you want the beta you should remove firefox-trunk, remove the PPA that MG&TL posted and instead add the PPA I linked to. Then just run a normal update through Update Manager and your Firefox will be upgraded to the beta version. When new versions hit the PPA you'll get them the same way, with your normal updates.

---

### Post by NickoHall on 2012-03-03
Thank you so much for that! It worked perfectly! :D
But I'm still confused as to why I couldn't execute the .sh :(

---

### Post by Paqman on 2012-03-03
No problem. It's always best to get your browser from a source that makes sure it gets updated regularly. That means the repositories or a trusted PPA. If you install it manually you'd have to do all the updates manually (which defeats half the reason to use Linux IMO).

---

### Post by NickoHall on 2012-03-03
Yeah well I didn't know about PPA, I thought you just had to install things like in windows but the PPA method is pretty cool! Thanks heaps! :)

---

