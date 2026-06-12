---
title: "programm cant acessdatabase, but works in guest mode, reinstallation wont help"
date: 2011-10-28
forum: General Help
---

### Post by JohannesJo on 2011-10-28
Im having problems with one of my favorite programms Nixnote. Without doing anything special it decided not to start anymore with the following message in a window named **qt jambi**:
```
Unable to connect to the database.

The most probable reason is that some other process
is accessing the database or NixNote is already running.

Please end any other process or shutdown the other NixNote before starting.

Exiting program.
```

Strangly its running as a guest user. I tried reinstalling it completly wiping out all user-data. Nothing worked out. Im guessing that something is messed up with the acces-rights for my usr-folder, as I also changed some login options before.

The problem is - being relatively new to ubuntu - I cant quite figure out what and how to fix it. Anyone got an idea how to figure out whats happening?

Edit: Also important to note: I compared all processes of guestmode and regular login and killed every 'extra'-process, but nixnote still doesnt start.

---

### Post by lluish on 2011-10-31
I've encountered same problem after upgrading from old eeebuntu and old nevernote (former name of nixnote) to new ubuntu 11.10 and new nixnote.

_If (and only if) you__ have your notes synced online at Evernote_, you could rename the local database folder (.nevernote folder in your user's home directory), restart nixnote, and sync it again. The program should download all your notes again to rebuild local database, and you are done. 

Instead, if you are using nixnote only as a local note manager, without syncing it online, this workaround won't work and would cause all your notes to get lost, so better not to try.


Good luck, hope it works for you as it did for me.

---

### Post by JohannesJo on 2011-11-01
Thank you! Somehow I forgot to delete the files in my home-folder... :-p Thought that synaptics would do the job, if told to.

Anyhow, I'm switching to wine+evernote now, as Nixnote sometimes likes to mess up...

---

### Post by JohannesJo on 2011-11-01
Thank you! Somehow I forgot to delete the files in my home-folder... :-p Thought that synaptics would do the job, if told to.

Anyhow, I'm switching to wine+evernote now, as Nixnote sometimes likes to mess up my notes and has some other bugs as well...

---

### Post by ajohnson2371 on 2012-07-01
I get the same issue with NixNote.
I renamed the directory, let it rebuild it, and I still get that error.

I think I shall also go the way of Wine + Evernote.

---

