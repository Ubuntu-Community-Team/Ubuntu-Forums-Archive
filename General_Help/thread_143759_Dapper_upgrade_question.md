---
title: "Dapper upgrade question"
date: 2006-03-13
forum: General Help
---

### Post by avantgardaclue on 2006-03-13
Hi folks, having spent the last 3 months converting to almost exclusive use of ubuntu i really don't want to have to do a clean install of dapper when it comes along. Tell me; i will be able to do a pure upgrade either online or from cd without losing any of my docs, settings progs and that this upgrade will be no less good than a new install?!?

tx simon

---

### Post by andrewsawyer on 2006-03-13
You should be able to do a dist-upgrade from Breezy to Dapper yes.

Personally I have always reinstalled, and given that I have a separate partition for my home documents this has never really been much of a problem for me.

When you dist-upgrade, just be aware that you will probably be in for a pretty big download.

---

### Post by manicka on 2006-03-13
hmmm, my recent upgrade went fairly well. A few hiccups that weren't to hard to fix. I would suggest being comfortable at the CLI and know how to fix X if you do it before the final release. That said though, this upgrade was far easier than the hoary to breezy upgrade where many crashed and burned... myself included.

As far as the clean install goes, if you have your home directory on a separate partition then you only have to do the clean install on your / partition and all your settings etc will be maintained in your home directory

---

### Post by avantgardaclue on 2006-03-13
[QUOTE=manicka]As far as the clean install goes, if you have your home directory on a separate partition then you only have to do the clean install on your / partition and all your settings etc will be maintained in your home directory[/QUOTE]

Right.... i don't think my home directory is on a seperate partition, basically i got so sick of trying to partion my C: drive i installed a 2nd hard disk and faultlessly installed on that. What do i need to do to

1 - create a seperate partition
2 - copy across my 'home directory'

Are all the progs i've downloaded stored in the home directory? It's not a deal breaker as i can easily install these progs again, it's my docs and things i don't wanna lose. Failing that, and thinking on the run maybe i could burn my home directory to a cd and reinstall after doing a fresh install... hmmmm

---

### Post by manicka on 2006-03-13
[QUOTE=avantgardaclue] thinking on the run maybe i could burn my home directory to a cd and reinstall after doing a fresh install... hmmmm[/QUOTE]

you certainly could do that but be sure include the hidden files and directories in the backup as well. This is where your various config and data files are kept for your desktop and program settings etc.

---

### Post by MJSOnline on 2006-03-13
Hi manicka.  Just a question.  How do I make my /home folder set to a diff partion, such as a 2nd hard drive in a folder of it own?  So something like - 2nddrive/user folders/home. Thanks in advance.  Matthew

---

### Post by andrewsawyer on 2006-03-13
From my understanding you should be able to edit the fstab file (sudo gedit /etc/fstab) and just add the location of the home directory.

Mine for example is:
```
/dev/sda3       /home           reiserfs defaults        0       2

```

And just copy all the files (inc hidden) over from your old home to the new one.

---

