---
title: "home ubuntu partition folder permission changed from fedora disable my login in ubunt"
date: 2009-10-13
forum: General Help
---

### Post by JimboCorn on 2009-10-13
i installed fedora11 on a 25G partition and the rest of my files are in a 135G partition with ubuntu installed , and i was changing the permissions from fedora so i could access to all of my files from fedora (now i know that i cant access to everything) but in the moment i change the permissions to root in fedora next time login in ubuntu it shows a message saying that home directory does not have the right permission etc etc ..well i used the recovery mode and used chmod to change the permissions back , well the next time i tried to login it shows me another message saying that home directory could not be found an ask me if a want to use root as home directory, i click yes and the only thing that shows is the default ubuntu desktop background and nothing else...

  These are the thing that i already tried:

- Look for the answer on google.
- look at this forum.
- use the recovery mode to enter but i cant find my original home drectory, i look for home and none of my files are there....

  i hope that someone can help me with this one....
-

---

### Post by quixote on 2009-10-15
This isn't going to be much help.  I had a similar situation once, normal access to /home was cut off, and it was a major hassle getting it sorted out.  I just cannot remember what I had to do. :rolleyes:  I'll keep searching around.  The good news is that the directory is still there, somewhere.  The bad news, at least in my case, is that I seem to remember reinstalling to finally fix the problem.

---

### Post by sirtrent on 2009-10-15
First thing you should should do is that when you're booted into Ubuntu make sure that your home partition is properly mounted. 

Next see if your old home directory is still there. As long as you havn't accidentally done anything too nasty your files should all still exist.

Also note, that I've found it's a good idea to have different usernames for each Linux installations sharing home space eg. adny (for Ubuntu) and andyf (for Fedora) (it sounds like you may have this).

Once you know that your home partition is being mounted, and your files exist you may have to change the permissions again:

I'm sure this is a big no-no for the paranoid, but this should rule out any issues you may be having related to permissions (You could then change it to 755 or so to let your Fedora user read but not write):
```
sudo chmod -R 777 /home/<YourUbuntuUsername>
```

(That will allow everyone all permissions to all your files)


Once you've done that you'll have to go into Administration->Users And Groups to change your Ubuntu user's home directory back its old one (/home/<YourUbuntuUsername>).

If all that works, next time you log out and back in your old desktop will reappear and everything should be good to go.

---

