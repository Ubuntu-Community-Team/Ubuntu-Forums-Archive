---
title: "what to backup on system"
date: 2009-07-28
forum: General Help
---

### Post by e24ohm on 2009-07-28
Folks:
what should I backup to save information and a user account with documents? If i want to save just the documents and related items, would it be safe to only backup the folders under "/home"?

---

### Post by SuperSonic4 on 2009-07-28
So long as you save all your documents in /home then yes: /home will suffice. Bear in mind this will copy program settings too so you may want to use a different folder.

On my system I have my documents on a separate partition (/mnt/Documents) and I save them there- the appropriate line is in fstab too so it mounts on boot

---

### Post by e24ohm on 2009-07-28
> **SuperSonic4 said:**
> So long as you save all your documents in /home then yes: /home will suffice. Bear in mind this will copy program settings too so you may want to use a different folder.

On my system I have my documents on a separate partition (/mnt/Documents) and I save them there- the appropriate line is in fstab too so it mounts on bootok thanks mate; however, what is fstab? what do i need to modify in order to get this to mount on boot?

---

### Post by philcamlin on 2009-07-28
> **e24ohm said:**
> ok thanks mate; however, what is fstab? what do i need to modify in order to get this to mount on boot?

The fstab (/etc/fstab) (or file systems table) file is commonly found on Unix systems as part of the system configuration.

and backing up home is all you need

---

### Post by SuperSonic4 on 2009-07-28
fstab controls what loads on boot - / , /home [if on a separate partition] and swap are mounted automatically.
Unless you frequently use different partitions you shouldn't need to touch fstab

---

### Post by e24ohm on 2009-07-28
> **philcamlin said:**
> The fstab (/etc/fstab) (or file systems table) file is commonly found on Unix systems as part of the system configuration.

and backing up home is all you need
ok understand thank you.

---

### Post by qchapter on 2009-07-28
For backup on my systems I usually just rsync my home directory to a backup drive.  Like the above post says the home directory typically contains user settings and user documents.

If you are not familiar with rsync type "man rsync" in a terminal window.

-Kevin

---

### Post by bodhi.zazen on 2009-07-28
Personally I keep a data partition separate from OS. I keep anything I want in that directory and so back up only the data partition.

As has been mentioned there are some config files in $HOME (.bashrc, .mozilla, etc) you want to back up, and others you do not need.

---

### Post by SuperSonic4 on 2009-07-28
> **bodhi.zazen said:**
> Personally I keep a data partition separate from OS. I keep anything I want in that directory and so back up only the data partition.

As has been mentioned there are some config files in $HOME (.bashrc, .mozilla, etc) you want to back up, and others you do not need.

The amount of time I've saved from backing up .bashrc must run into hours by now XD. Most of the others I do not mind so much - especially since I put most things on a different partition

---

### Post by ajgreeny on 2009-07-28
Just out of interest, other than perhaps some aliases you may have added yourself to the .bashrc file, what else have you edited in it to save you the hours you speak of?

---

### Post by bodhi.zazen on 2009-07-28
Personally I have a few personal functions in .bashrc

I prefer zsh, and I find .zshrc is a bit more complex

[http://bodhizazen.net/adblock/bashrc](http://bodhizazen.net/adblock/bashrc)
[http://bodhizazen.net/adblock/zshrc](http://bodhizazen.net/adblock/zshrc)

as you can see, it is not really my zshrc, but looking it over I have made enough changes such that it is worth backing up. I can say it would take some time to re-create from scratch.

---

### Post by SuperSonic4 on 2009-07-29
> **ajgreeny said:**
> Just out of interest, other than perhaps some aliases you may have added yourself to the .bashrc file, what else have you edited in it to save you the hours you speak of?

Most of time comes from remembering the aliases. Plus I have some nifty colours

---

### Post by e24ohm on 2009-07-29
So, if I do not have any configurations that I need to keep, then I can just backup a directory that I save my data to? If I understand this, then this is great.

Hmmm, now I have custom made bash scripts, which I placed in a directory so i can you the script from any location; however, I forget where i placed these files. Can anyone offer suggestions, on where this location might be...I totally forget, and I'm not sure where to start looking or researching the locations.

thank you
E

---

### Post by SuperSonic4 on 2009-07-29
Scripts are likely to be in ~/bin or /usr/bin -  you may find some by typing ```
which <script>
```

> So, if I do not have any configurations that I need to keep, then I can just backup a directory that I save my data to?

Yes. If you save it all to ~/Docs then you need only back up ~/Docs

---

### Post by e24ohm on 2009-07-29
> **SuperSonic4 said:**
> Scripts are likely to be in ~/bin or /usr/bin -  you may find some by typing ```
which <script>
```



Yes. If you save it all to ~/Docs then you need only back up ~/Docsthank all of you for helping me out, and taking the time.....all of you are great...

One more question...I am looking at tape drives, and I have been reading the difference between AIT, DLT, DAT, and LTO. I understand Sony developed the AIT (bata tapes again), and DLT and LTO are comparable; however, which type format should I go with? Which tape drive will/would be use enterprise/production environment? Is AIT good or is this the Bata tape of the computer world?

thank you.

---

### Post by ajgreeny on 2009-07-29
> **SuperSonic4 said:**
> Most of time comes from remembering the aliases. Plus I have some nifty colours
That's what I suspected, though in my case I have all my aliases in .bash_aliases rather than .bashrc.  It just makes life easier in my opinion.

Incidentally, I had never heard of zsh or the .zshrc file before.  You live and learn.

---

### Post by bodhi.zazen on 2009-07-29
> **ajgreeny said:**
> That's what I suspected, though in my case I have all my aliases in .bash_aliases rather than .bashrc.  It just makes life easier in my opinion.

Incidentally, I had never heard of zsh or the .zshrc file before.  You live and learn.

If you have not tried zsh, and you have an interest, check it out

[http://friedcpu.wordpress.com/2007/07/24/zsh-the-last-shell-youll-ever-need/](http://friedcpu.wordpress.com/2007/07/24/zsh-the-last-shell-youll-ever-need/)

I gave it a 1 week trial. After 2 days I preferred zsh to bash.

---

### Post by e24ohm on 2009-07-29
> **bodhi.zazen said:**
> If you have not tried zsh, and you have an interest, check it out

[http://friedcpu.wordpress.com/2007/07/24/zsh-the-last-shell-youll-ever-need/](http://friedcpu.wordpress.com/2007/07/24/zsh-the-last-shell-youll-ever-need/)

I gave it a 1 week trial. After 2 days I preferred zsh to bash.so zsh is another form of BASH?

---

### Post by bodhi.zazen on 2009-07-29
It is an alternate shell, yes.

---

### Post by e24ohm on 2009-07-30
> **bodhi.zazen said:**
> It is an alternate shell, yes.I will have to check it out. A week ago I was learning BASH scripts; however, my instructor did not teach us about zsh.

---

