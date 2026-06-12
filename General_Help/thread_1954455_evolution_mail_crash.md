---
title: "evolution mail crash"
date: 2012-04-08
forum: General Help
---

### Post by panronnie on 2012-04-08
my evolution mail crashes when i start it up and it try,s to pick up my mail

i tried starting it up in terminal 
with the following result 

ronald@ronald-desktop:~$ evolution
Migrating cached data
  mv /home/ronald/.evolution/cache/http /home/ronald/.cache/evolution/http
  FAILED: Map is niet leeg
  mv /home/ronald/.evolution/cache/tmp /home/ronald/.cache/evolution/tmp
  FAILED: Map is niet leeg
  rmdir /home/ronald/.evolution/cache
  FAILED: Map is niet leeg (contents follows)
          tmp
          http
Migrating config data
Migrating local user data
  rmdir /home/ronald/.evolution/tasks
  FAILED: Map is niet leeg (contents follows)
          tasks
  rmdir /home/ronald/.evolution/cache
  FAILED: Map is niet leeg (contents follows)
          tmp
          http
Segmentatiefout
ronald@ronald-desktop:~$ 

any help greatly appreciated as i have not backed up my mail and adressbook

---

### Post by panronnie on 2012-04-12
have run it under gdb
then it stays running
but with a lot of reports

---

### Post by Jonners59 on 2012-05-10
Same issue.  I have been using Evolution for a couple of years now and since the upgrade to 12.04 it will not stay open.  tried re-install to no avail.

---

### Post by sunbird on 2012-05-15
I have a slightly different issue, but related. On a recent clean-install of 12.04, I migrated my home directory and, at first, evolution worked great -- way less buggy than 10.04. But now, I cannot delete any messages.

My system is fully up-to-date.

I am using evolution to access my workplace's exchange 2003 server, which worked in 10.04, but now, I can only read messages, I cannot delete them.

I've tried purging the packages and reinstalling. No dice. I've also tried deleting ~/.config/evolution and ~/.local/share/evolution. Strangely, the program still starts up without having to run the setup manager. Where are evolution user files stored? It used to be .evolution, but not anymore.

---

### Post by Jonners59 on 2012-05-15
Yes, it is the same but different if that makes sense.  The configs and stuff have moved since 10:04.  I think that is when it was.  That is when mine started to fail.  They have moved from the old file system to a db system.  I did have a list of the three locations, but I dare not delete anything without someone who knows what they are doing giving advise.  It seems to me that MAYBE you have the same issue that an existing config does not work in the new environment, but you can not get rid of the old to start a-new....

If I find the info I shall update this reply.

FYI:
[HTML]The user's data files$HOME/.local/share/evolution
Various configuration and state files$HOME/.config/evolution
Disposable data caches$HOME/.cache/evolution
Configuration settings in GSettings$HOME/.config/dconf
[/HTML]

---

### Post by sunbird on 2012-05-16
Unfortunately, even if I clean out all the user files and set it up as a brand-new user, I still cannot delete messages.

This is extremely frustrating and I never had this problem in 10.04, same hardware, same mail server.

Any ideas?

---

