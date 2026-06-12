---
title: "users in evolution"
date: 2006-05-03
forum: General Help
---

### Post by bbarrons on 2006-05-03
I would like to be able to setup users in evolution. My wife and I use seperate accounts for home and work.
 I like evolution better than thunderbird but in thunderbird you can use profiles. I prefer not to use outlook in crossover. IS this possible with evol? maybe a plugin or something. the help section is a bit sketchy on this.... or I am blind.....
also.... I am running dapper right now and if I didnt already know it was still in the testing phase I would never have guessed. It runs better on my 3 boxes than any other distro I have tried over the last couple of years......
thanks all
 Bill

---

### Post by dcstar on 2006-05-03
[QUOTE=bbarrons]I would like to be able to setup users in evolution. My wife and I use seperate accounts for home and work.
 I like evolution better than thunderbird but in thunderbird you can use profiles. I prefer not to use outlook in crossover. IS this possible with evol? maybe a plugin or something. the help section is a bit sketchy on this.... or I am blind.....
......
 Bill[/QUOTE]
Just set up separate Ubuntu logins, problem solved.

---

### Post by AndyCooll on 2006-05-03
Not quite following what you are wanting to do.

Are you saying that you want it so that when Evolution opens it asks which users e-mail to view, i.e. your wifes or yours? If that is the case then as dcstar says it would be far better to have separate logons to your Linux box itself. So when you logon and open up Evolution it has your settings. If your wife logs on and opens up Evolution it displays her e-mail accounts. You don't even need to log one user off before logging the next one on. You can simply "switch" user.

Or are you saying that you want to separate your e-mail accounts (i.e. your work one and your home one? If that's the case then I believe Evolution enables you to have different profiles (can't check this at the moment as I'm at work).

:cool:

---

### Post by bbarrons on 2006-05-03
I would like to be able to start evol and then have it ask which account to start.thunderbird uses profiles and outlook uses users when starting. I have her setup with her own desktop its just a pain to log back and forth or switch users when the only thing I need to do is open a user.
YEs, being able to select a profile to keep work and home email is also a goal for my wife and I. I didnt see anything in evol to do this but then again I might have just missed it.
  I am also working on getting our parish school to start using ubuntu in the classroom. Most classrooms have win98 in them and ubuntu would be far better for them. SO, before I present it to the teachers I want to be well versed on all the features...
p,s, thanks for the very quick replies...always appreciated.
 Bill

---

### Post by SreckoMicic on 2006-05-03
See preferances and then add account.

---

### Post by bbarrons on 2006-05-03
nope. preferences, then add account just adds a new location to recieve mail. If I setup this way then my mail and my wifes mail and home and office all will come in under the same set of folders. it wont seperate the mail. I know this can be done with filters but it shouldnt have to be that way. evol is a full featured email client that should be comparable to outlook. If someone in a bus env wants to use it with ms exchange than this feature should be vail. when more than one user uses a pc the choice should be at software startup to select a profile and open up your mail. This is avail in mozilla thunderbird, poco and a few others besides in outlook.

---

### Post by nocturn on 2006-05-03
Why not run evolution as here user?

I mean, log into your desktop and use the runas (if it's still there) or su to run evolution with ther account.  That way mail gets stored in the right place etc.

You can also install ssh-server and connect to localhost (if you don't want passwords, set up public keys). 
```
ssh -X youwifesuser@localhost 'evolution' 
```
will do the trick

---

### Post by nocturn on 2006-05-03
[QUOTE=bbarrons]when more than one user uses a pc the choice should be at software startup to select a profile and open up your mail. This is avail in mozilla thunderbird, poco and a few others besides in outlook.[/QUOTE]

The difference is that Evolution only runs on *nix systems, which always had the multi-user features.   So evolution can safely assume that mail is automaticly seperated by saving it to the current HOME directory.  

Thunderbird etc are multi-platform, so it can not make the same assumption.

---

### Post by bbarrons on 2006-05-03
ssh did what  Iwanted it too. Thanks for the reply. Now we can both have our email up and running .
thanks again
Bill

---

