---
title: "Xubuntu stops at login, debug/detail"
date: 2010-05-17
forum: General Help
---

### Post by copb.phoenix on 2010-05-17
Please forgive nominal errors in this post; I have to use a Nintendo Wii to post it.

My Ubuntu Lynx install has the xubuntu-desktop package installed. Just recently I created a new user to give guests some space, and to use at work.

What happens is, as soon as it gets to the login manager, it fails to load the list of users, but appears to try multiple times. The piece of GUI in the center of the screen just sort of blinks in and out.

During startup, reading the logged process gives me this:

(process:280): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)

[rest scrolls by too quick to catch]


Given that I have no way to burn a cd, and never made an install disc (Live-USB installation, since replaced), can anyone lend a hand?

I know I sound new to this, but I'm actually going to college for IT and game design, so I don't mind command line solutions from the world of Vi.

---

### Post by copb.phoenix on 2010-05-18
While I realize this is a double post, I see no standards for it on this forum (I'm sure there are, and I'll gladly lend an ear to someone wanting to tell me)...

Anyway, there is an update on this situation.

I was able to get the Live-USB together again, so I can now run Ubuntu 10.04 live. So, now there are two possible ways for me to solve this problem that I'm very willing to accept:

1) Retrieve some files out of my original user $HOME directory, which I cannot do right now because it keeps giving me "Permission denied" on it... Is there any way to unlock it using my original password? At least I've gotten this far... But, if I could retrieve those files, which are less than 100 MB total in size, then I'm not afraid to reformat the system and start from scratch. I'm able to do the re-installation myself - I'd only need help figuring out how to retrieve the files.

2) Somehow fix my login. I'm more than willing to delete the erroneous user, or otherwise make it so that the system is unaware that the user exists. However, I reach the problem of being able to read many of my configuration files, but not edit them without authenticating. Whether this is in the file system or just part of the Live-USB, I'm uncertain. Not to mention, I don't actually know all the files that get changed when you ask Ubuntu to add a user via the GUI interfaces.

Really, anything is alright, I just need to solve this problem one way or another with those files intact within a couple days, which is why I'm so frantic.



EDIT:

After a brief session or four of messages passed between me and the people those files belong to, I'm going to go ahead and reinstall my Ubuntu install. However, while this is no longer a "crisis omg help" topic, I am still interested in learning about this situation, and the solutions to the problems involved in case it happens to me, a friend, a coworker, or one of my lab students in the future. I'll mark this as solved after the reinstall, in case something happens between now and then.

---

### Post by anglican on 2010-05-18
> **copb.phoenix said:**
> Please forgive nominal errors in this post; I have to use a Nintendo Wii to post it.

My Ubuntu Lynx install has the xubuntu-desktop package installed. Just recently I created a new user to give guests some space, and to use at work.

What happens is, as soon as it gets to the login manager, it fails to load the list of users, but appears to try multiple times. The piece of GUI in the center of the screen just sort of blinks in and out.

During startup, reading the logged process gives me this:

(process:280): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)

[rest scrolls by too quick to catch]


Given that I have no way to burn a cd, and never made an install disc (Live-USB installation, since replaced), can anyone lend a hand?

I know I sound new to this, but I'm actually going to college for IT and game design, so I don't mind command line solutions from the world of Vi.
Can't you just boot in recovery mode and undo whatever it was you did to install this new user (probably just removing the entry from /etc/passwd and /etc/shadow should do it)?

H

---

### Post by copb.phoenix on 2010-05-18
> **anglican said:**
> Can't you just boot in recovery mode and undo  whatever it was you did to install this new user (probably just removing  the entry from /etc/passwd and /etc/shadow should do it)?


Unfortuantely, I never learned how to do that. While I'm far from new to  *coding* in a *nix environment, I'm still a long shot from being  used to *living* in one.
   
   Testing that works to remove a user for all practical intents and purposes (well, a blank user, with no personal files). It's very possible that the same actions would leave behind the user's personal files in their $HOME directory, though I wouldn't swear to it.

If this ever occurs again, I'll be sure to try that. I hadn't realized that GRUB still had a functional menu, even with only one system to choose from. Meanwhile back, nothing went wrong with the install, so this is marked as solved. I'm sorry to waste people's time.

---

