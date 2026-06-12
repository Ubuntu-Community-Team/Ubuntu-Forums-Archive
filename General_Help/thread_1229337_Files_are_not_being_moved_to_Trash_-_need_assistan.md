---
title: "Files are not being moved to Trash - need assistance !"
date: 2009-08-02
forum: General Help
---

### Post by credobyte on 2009-08-02
Lately ( in the past few days ) I've mentioned that if I delete something from my home directory, files are not being moved to trash - they simply disappear. 
How do I fix this ? Oh, and .. how do I verify that these files are still not on my PC ( somewhere in the "invisible" part of the Trash ) ?

---

### Post by SteveDee on 2009-08-02
> **credobyte said:**
> Lately ( in the past few days ) I've mentioned that if I delete something from my home directory, files are not being moved to trash - they simply disappear. 
How do I fix this ?.....

Have a look at the options in Nautilus menu Edit > Preferences > Behaviour > Wastebasket

---

### Post by credobyte on 2009-08-02
> **SteveDee said:**
> Have a look at the options in Nautilus menu Edit > Preferences > Behaviour > Wastebasket

Everything seems to be as usual. Any other ideas ? I've deleted approximately 10GB in the past few hours - Trash is still empty ( even after 3 restarts ) :(

---

### Post by PGScooter on 2009-08-02
What are you using to delete? nautilus? and then you just click the delete button? Maybe they are in your trash but nautilus incorrectly displays the trash. Check teh folder ~/..local/share/Trash/files/

the way to make sure that they're still not on your pc is to make a unique filename, say uniquefilename121 and then delete it and search for it:
```

touch uniquefilename121 #this just makes an empty file
# delete however you delete (nautilus?)
sudo find / -name uniquefilename121

```
the search will take awhile cause it is searching absolutely everywhere.

---

### Post by credobyte on 2009-08-02
Crap! All the files are still there and I can't remove them by clicking "Empty Trash" :twisted: How to fix it ( yeah, I can delete them manually, but .. that's not the way it should be ) ?

---

### Post by PGScooter on 2009-08-02
ok, so from what I understand, the files are correctly being moved to the trash, but are not being displayed in the trash folder right?

Please answer the question of if you are using nautilus? If you don't know, I can tell you how to find out.

If you are using nautilus, I would try reinstalling it. Be sure to back up data and any settings, just in case. That should restore the trash viewing correctly.

Also, if you have time and want to help, filing a bug report would be great!

---

### Post by credobyte on 2009-08-02
> **PGScooter said:**
> ok, so from what I understand, the files are correctly being moved to the trash, but are not being displayed in the trash folder right?

Please answer the question of if you are using nautilus? If you don't know, I can tell you how to find out.

If you are using nautilus, I would try reinstalling it. Be sure to back up data and any settings, just in case. That should restore the trash viewing correctly.

Also, if you have time and want to help, filing a bug report would be great!

Yes, I'm using Nautilus ( can't stand Dolphin :p ). Files are being moved correctly ( found it only now ) but Trash applet doesn't seem to work ( eg., Trash is always empty and I can't clean it ).

---

### Post by PGScooter on 2009-08-02
i have to go on a trip, but I will check back in a few days just to make sure you got it figured out. If not, I will help you some more until we solve this annoying hiccup! best of luck!

---

### Post by PGScooter on 2009-08-02
ok, then i would suggest reinstalling. There shouldn't be any problem, but I always reccommend backing up.

An alternative is to just make an alias for the command "rm ~/.local/share/Trash/files/*" so whenever you want to empty trash you just run that command. If you want to try this, put this line of code in your ~/.bashrc file:
```
alias empty='rm ~/.local/share/Trash/files/*'
```
the exit all terminals, open a new terminal, and type "empty" as a command. that should do it.

---

### Post by credobyte on 2009-08-02
Problem solved - reinstalled Nautilus and everything seems to be fully working :)

---

