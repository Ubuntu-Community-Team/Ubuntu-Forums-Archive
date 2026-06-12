---
title: "Ubuntu Netbook Remix 10.10 - remove annoying feature"
date: 2010-10-30
forum: General Help
---

### Post by triunenature on 2010-10-30
Soo, i just installed UNR 10.10 on my computer, everything runs well enough.  Way slower than 10.04... but thats the price we pay for making our systems "prettier" i guess.

Anyway, the "Files & Folders" section has an "Recent" section where it shows recently opened files/folders.  I just need that gone.

That ***_or_*** remove the "Files & Folders" section from the quick launch bar... I have Nautilus on quick launch, which i prefer to there new crappy, slow, annoying, buggy file manager called; "Files & Folders".

Thanks in Advance

---

### Post by kerry_s on 2010-10-30
there's no choice, i just ignore that icon, it's useless like the trash icon.

---

### Post by triunenature on 2010-10-30
> **kerry_s said:**
> there's no choice, i just ignore that icon, it's useless like the trash icon.

Thats new... A linux person telling that linux isn't giving me a choice.  Surely you guest.

Really, there has to be a better option than to ignore it.  If i must, i will start using ubuntu 10.10 Desktop, untill they give me options back...  But i really think one of you smart people can show me how to remove it... its just an icon, how hard is it to make it go away?

---

### Post by kerry_s on 2010-10-30
it's the first release of unity & as such it's work in progress. i would love to remove those icons.

whoo, i just noticed they got right click actions, when did that happen? lol
does it do that in 10.10? (see pic's)

i updated mine to natty(11.04) just to see what changes would be coming.

---

### Post by triunenature on 2010-10-30
> **kerry_s said:**
> it's the first release of unity & as such it's work in progress. i would love to remove those icons.

whoo, i just noticed they got right click actions, when did that happen? lol
does it do that in 10.04? (see pic's)

i updated mine to natty(11.04) just to see what changes would be coming.

10.10 i can right click the icons ("Files & Folder" and "Trash"), though i don't have as many options as you...

I hate to be the downer, but UNR 10.04 (i think thats the right ver.) was way better.  "Files & Folders" crashes more than it loads...  and this computer runs 1/2 the speed.  Dare i say it, i think windows 7 runs faster than unr 10.10...  :(

---

### Post by ajgreeny on 2010-10-30
Why don't you simply try the gnome desktop session of 10.10 UNR, it is already installed and available to you.  To be honest, I think a lot of people install the UNR version and then just move to the already installed gnome desktop from the sessions menu on the login window.

Certainly that is how I work mine; I just find the UNR desktop of 10.04 counter-intuitive.  Having also seen and tried the unity desktop of 10.10, I find myself completely baffled at the moment, though I admit to not really trying it for very long.

---

### Post by triunenature on 2010-10-30
> **ajgreeny said:**
> Why don't you simply try the gnome desktop session of 10.10 UNR, it is already installed and available to you.  To be honest, I think a lot of people install the UNR version and then just move to the already installed gnome desktop from the sessions menu on the login window.

Certainly that is how I work mine; I just find the UNR desktop of 10.04 counter-intuitive.  Having also seen and tried the unity desktop of 10.10, I find myself completely baffled at the moment, though I admit to not really trying it for very long.

How?

Do i need to logout then log back in?? 

Please explain this magic!

---

### Post by CoolJohnB on 2010-10-30
yes you log out, before logging back in on the bottom bar you have a choice, just select desktop and log back in, problem gone away!

---

### Post by triunenature on 2010-10-30
> **CoolJohnB said:**
> yes you log out, before logging back in on the bottom bar you have a choice, just select desktop and log back in, problem gone away!

GOD i love you!  Can i marriz you?

You have saved me so much grief.

I am not calling this problem "Solved" because i want to use UNR, but i can't with the "recent" showing up when i open "Files & Folders".  Surely one of you amazing people can find a real answer to it!

How hard is it to delete an icon?

---

### Post by triunenature on 2010-10-30
Bump for justice!

Soo, I have made progress... but none worth mentioning...

Any ideas on how to remove "Files & Folders" Icon?  Or just stop "Recent" from being displayed?

---

### Post by triunenature on 2010-10-30
Same question... new idea.

How does ubuntu know what files i recently opened?  There must be some cache or log file with the names in there... Does anyone know the location of this file?  If so, i can just write a script to auto delete that log file. Or create an invalid log file in its place, under root, to stop it from being able create a new log.

Any help?

---

### Post by triunenature on 2010-10-31
Selfless bump.

Does anyone know where the log file is, that says what files where opened recently?

Thanks

---

### Post by Verbeck on 2010-10-31
in your home folder, there should be a file named .recently-used.xbel

---

### Post by triunenature on 2010-10-31
> **Verbeck said:**
> in your home folder, there should be a file named .recently-used.xbel

Thank you SOOO much!!!

However... it doesn't work.  I mean, yes the file did exist, and i did delete it.  However when i opened "Files & Folders" back up, it showed the recently opened files...

I restarted my computer, and tryed to delete the file again, but alas, it said it didn't exist (due to the obvious fact i JUST deleted it). And the "Files & Folders" app still showed recent files accessed.

Soo, next question.  Is there another log file that holds recently opened files?  Or again, and someone show me a way to remove that icon?

---

### Post by Verbeck on 2010-10-31
in the terminal try 
```

rm ~/.recently-used.xbel 
touch ~/.recently-used.xbel 
sudo chattr +i ~/.recently-used.xbel

```from [http://ubuntuforums.org/showthread.php?t=66821](http://ubuntuforums.org/showthread.php?t=66821)

edit : tried on by 10.10 desktop and works (ext4 file system)

---

### Post by kerry_s on 2010-10-31
it's-> ~/.local/share/zeitgeist

hold on let me test, be back.

yeap, that's the folder. i don't know which file & locking the folder gives a empty icon. see pic

---

### Post by triunenature on 2010-11-01
> **Verbeck said:**
> in the terminal try 
```

rm ~/.recently-used.xbel 
touch ~/.recently-used.xbel 
sudo chattr +i ~/.recently-used.xbel

```from [http://ubuntuforums.org/showthread.php?t=66821](http://ubuntuforums.org/showthread.php?t=66821)

edit : tried on by 10.10 desktop and works (ext4 file system)

Didn't work for me, actually didn't do anything...
(ext4 file system --> unr 10.10 complete install)

> **kerry_s said:**
> it's-> ~/.local/share/zeitgeist

hold on let me test, be back.

yeap, that's the folder. i don't know which file & locking the folder gives a empty icon. see pic

Failed. Nothin' happened.

Oddly enough, for one moment, "Files & Folders" showed as completely empty... but then i reopened it, and everything was back to normal...

I did:

```
chmod 000 -R ~/.local/share/zeitgeist
```

Got any other ideas?  Really this shouldn't be difficult...

Btw --> This is a fresh install of UNR ... the only difference is, i didn't install english as the default language...but that shouldn't effect anything...

---

### Post by triunenature on 2010-11-01
Well, the good and the bad.  I am calling this thread "solved", yet i still have a bad taste in my mouth...

I, through all of your wonderful help, have completely disabled files and folders... yet the icon still exists...

At least it doesn't show recent anymore... (nor anything else for that matter)

Hopefully, someone on the developement team, will read this and allow us to decide what goes on the side bar, and if we so choose to use the "Files & Folders" thing.. allow us to decide what catogories are displyed on there.

Till next time... thanks again!!

Omega

---

### Post by Verbeck on 2010-11-01
> **triunenature said:**
> Well, the good and the bad.  I am calling this thread "solved", yet i still have a bad taste in my mouth...

I, through all of your wonderful help, have completely disabled files and folders... yet the icon still exists...

At least it doesn't show recent anymore... (nor anything else for that matter)

Hopefully, someone on the developement team, will read this and allow us to decide what goes on the side bar, and if we so choose to use the "Files & Folders" thing.. allow us to decide what catogories are displyed on there.

Till next time... thanks again!!

Omega
i don't think the devs comes to the forums. how about filing a bug report at launchpad? or try [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

---

