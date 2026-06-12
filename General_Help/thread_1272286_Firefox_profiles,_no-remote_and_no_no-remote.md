---
title: "Firefox profiles, no-remote and no no-remote"
date: 2009-09-22
forum: General Help
---

### Post by qbxk on 2009-09-22
I'm in a unique situation where I need a certain firefox profile to start when the user is logged in (so that a webapp will be running, but not in the "standard" firefox profile they will use to surf with), and thereafter use a different firefox profile when they click any of the several launchers (one on the panel, one on the desktop, one in the apps menu)

I've been through over and over many of the -P and the -no-remote options, but I can't seem to get this to work the way we require.

I have in system->preferences->sessions, startup programs a command to start the firefox that will launch the profile that will run the webapp, the command is 
```
firefox -P "WebappProfile" -no-remote
```

Then the launchers that will run the regular firefox, are all configured to have the command 
```
firefox -P "RegularUserProfile"
```

My profiles.ini contains 
```

[General]
StartWithLastProfile=0

[Profile0]
Name=RegularUserProfile
IsRelative=1
Path=XXXXX.RegularUserProfile
Default=1

[Profile1]
Name=WebappProfile
IsRelative=1
Path=XXXXX.WebappProfile

```

The problem is that once logged in, the webapp instance starts fine, but clicking on launchers starts another window using the WebappProfile for reasons I can't explain.  This appears to go against the documented behavior IMO.  The only way to get a firefox instance launched is to run a firefox command with '-no-remote' in it, to force that RegularUserProfile to become "active"

I understand that I could put -no-remote into the launchers, but if I do this, then you couldn't say, just click the launcher icon while your regular firefox window is already open b/c it will give you the "firefox is already running error"

I'm open to creative solutions, including somehow automating that first "no-remote" run, to force it to using the RegularUserProfile, however I cannot ask the users to do this themselves.  I need to be able to FORCE a particular profile to open, irregardless of which profile may already be open (the webapp may need to be restarted from time to time as well)

This has become extremely frustrating thanks for any help you can provide, let me know if I can answer any questions.

All of the above is true for both firefox 3.0.14 (as installed by apt-get on an up-to-date 8.04 LTS) and a firefox 3.5.3 freshly downloaded from mozilla. 

](*,)

---

### Post by lovinglinux on 2009-09-22
Unfortunately, that's Firefox normal behavior.

What I suggest is to use [prism](apt:prism) instead. Have you tried it?

What kind of web app and profile configurations do you need? Do you need a particular extension to run in this profile or can it be just a vanilla Firefox?

---

### Post by qbxk on 2009-09-22
ick, alright, that makes no sense

I'll give prism a shot, thanks for your reply

---

