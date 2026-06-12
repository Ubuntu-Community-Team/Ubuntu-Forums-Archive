---
title: "A few problems for a Ubuntu noob"
date: 2010-04-30
forum: General Help
---

### Post by Ysbl on 2010-04-30
I have two problems.

1. I tried to install vuze, but I can't. I extracted the tar.bz2 file to desktop, and I put **sudo apt-get install vuze** and **sudo apt-get install azureus** in the terminal but it said packages were missing.

2. I can't install Java JRE at all.

Thanks, Ysbl

---

### Post by cogier on 2010-04-30
First of all if you want to run Windows programmes I suggest you use Windows.

You need to learn a little more regarding installing software with Ubuntu. Start with the **Ubuntu Software Centre**. If you want to install other software not available there you need other skills. Have a look on the net for further help.

It takes time to unload the Windows thinking that many of us got used to. Linux is different - Give it time and you will see the advantages, as well as the disadvantages.

Enjoy Ubuntu - It IS good.

---

### Post by Shadow12313 on 2010-04-30
You can install vuze via synaptic and windows games can usually run under programs like crossover office games and cedega.  And to install java try this article [http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html]("http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html")

Hope this helps.

---

### Post by Ysbl on 2010-04-30
> **cogier said:**
> First of all if you want to run Windows programmes I suggest you use Windows.

You need to learn a little more regarding installing software with Ubuntu. Start with the **Ubuntu Software Centre**. If you want to install other software not available there you need other skills. Have a look on the net for further help.

It takes time to unload the Windows thinking that many of us got used to. Linux is different - Give it time and you will see the advantages, as well as the disadvantages.

Enjoy Ubuntu - It IS good.

I like Ubuntu, so I think I'll do a Dual-Boot, Windows for games, ubuntu for everything else.

---

### Post by KinKiac on 2010-04-30
Im a bit of a noob myself but i can tell you a couple things.  First, the **sudo apt-get** commands, are for software that is in the repositories.  If it isnt in there then those wont work.  Ive never tried to install Vuze before on linux( I gave up them a while back on windows about the same time it became Vuze and started using utorrent instead) but if it came as an archive go into the extracted folder and look for a readme file or setup file, or some other text file and you may find the directions for installing.  

In many cases what you want to do is extract to a folder in your home directory.  Then open a terminal window and browse to that directory (eg cd ~/home/username/vuze  replacing vuze with the name of the folder you extracted to)  

Once in the directory with all the install files you will normally have to type

```
./configure (sometimes but not always)
make
sudo make install
```

This is a pretty common way of installing programs that are downloaded as archives, its how you install from source in most cases(anyone feel like correcting me on this please do as Im a bit of a noob myself).  Just look for the readme and install directions in a text file and it should give you the proper commands which will be something similar to what i wrote above.  

#2 I cant help you with, sorry
#3 Sorry again, in my experience it is better to keep a windows install around as a dual boot if you plan on doing any serious gaming.  

Hope that helps.  Im sure someone else will be around who knows more than me if not.

---

### Post by GSF1200S on 2010-04-30
> **Ysbl said:**
> I have three problems.

1. I tried to install vuze, but I can't. I extracted the tar.bz2 file to desktop, and I put **sudo apt-get install vuze** and **sudo apt-get install azureus** in the terminal but it said packages were missing.

2. I can't install Java JRE at all.

3. None of my windows games work through Wine or PlayOnLinux.

Thanks, Ysbl

1) What version of Ubuntu did you install? Azureus is available in the repos, so you shouldnt even need to download it. When you enter the install command, what does it say? Post the output here.
2) Enable the Ubuntu Lucid Partner repos (containing the URL [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)) in System>Administration>Software Sources>Other Software, let it reload and close. Then, install sun via Synaptic Package Manager.
3) That sucks. If the game companies designed games for linux, we wouldnt have this problem. If you need them and wine cannot run them, then I guess youll need to use windows for them. This is a problem with capitalism, not Ubuntu. If you take a look at the wine appdb, it might give you helpful suggestions for getting your games to work (or tell you whether its currently possible).

---

