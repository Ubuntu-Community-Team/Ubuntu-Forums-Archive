---
title: "Update mgr. issue"
date: 2010-02-19
forum: General Help
---

### Post by Barney Oatmeal on 2010-02-19
Keep getting stuck in update manager - this is the error message.....

Anybody got ideas?

Can I find the update that isn't working somehow and ditch it without losing the good ones?  

Thanks and Blessings,
                      Barney Oatmeal

[IMG]http://i178.photobucket.com/albums/w249/daytonalilbit/Screenshot-Changesapplied.png[/IMG]

---

### Post by Barney Oatmeal on 2010-03-08
Isn't there a thread on how to fix update manager ills?
I can't seem to find one....... can someone please direct me?

---

### Post by lindsay7 on 2010-03-09
Did you try sudo update-manager -d

be careful because you will be offered the update to 10.4 at the top of the screen.  It is too early to do that at this time.

---

### Post by Barney Oatmeal on 2010-03-13
Lindsay7 - tried it that way, same error message.
Looks to be an issue with the debian package manager, if I read the error correctly....... anyone have a direction in which to point me, please?

Blessings,
          Barney Oatmeal

---

### Post by Miljet on 2010-03-13
It appears that there is some problem with the /var/lib/dpkg/available file. There should also be a file called available-old in the /var/lib/dpkg subdirectory. First thing I would do is check to see if those files are identical. If not, perhaps renaming available to something else and renaming available-old to available and see what happens. 

If that changes nothing, rename them to available-old1 and available-old2. Then run update manager to see if it will rebuild the file from scratch.

Mind you, I haven't tried any of this myself but it does not seem anyone else is anxious to jump in with advice, so I am just giving you something to think about. Renaming files is a relatively safe experiment since you can always restore them to their previous names if it doesn't help.

You might also want to just scan through the available file to see if you spot any obvious errors. It is a rather long file so you will want to filter it through the less command. ```
cat /var/lib/dpkg/available | less 
```

---

### Post by Barney Oatmeal on 2010-04-29
Have tried what you suggested, but cannot alter the file in any way - cannot move it, it will not open beyond about 1/4 of the way before an error message saying there is a problem opening the file.

I surely don't want to have to reinstall, but that'll be next if I don't get some help.

Thank you so much for the effort!!

Blessings,
          Barney Oatmeal

---

### Post by Barney Oatmeal on 2010-05-29
Reinstalled.

---

### Post by bildr on 2010-05-29
sorry dude, i would have helped but i didn't see that thread

---

