---
title: "Pidgin Problem"
date: 2009-08-23
forum: General Help
---

### Post by XicoXperto on 2009-08-23
when I connect trough pidgin to my msn it shuts down, does anyone knows what might that be?

---

### Post by DFlame on 2009-08-23
Are you running the latest version with an updated system? Open a terminal window and run these commands:

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

Then try again. Post back with the version of Pidgin in question and any settings/plugins you have enabled which may be relevant if the problem persists :)

---

### Post by XicoXperto on 2009-08-24
its all up to date.
Pidgin 2.5.5

just chose msn on the protocol and put the user name and password.


on advanced is:
server - messenger.hotmail.com
port - 1863
http method server: gateway.messenger.hotmail.com
show custom smiles: enabled
proxy: USE GNOME PROXY SETTINGS 
(i have switch to no proxy, and still the same problem)

thank you for help

---

### Post by jesuisbenjamin on 2009-08-24
Is your problem related to this? [http://ubuntuforums.org/showthread.php?t=965444](http://ubuntuforums.org/showthread.php?t=965444)
I used not to be able to connect to msn with pidgin. The work around in the end was to get a access on msn protocol with my gmail ID.

---

### Post by XicoXperto on 2009-08-24
not really it stoped work when i changed that it didnt logged...
i see it log, i can see friend list starting to show up, and then it closes...

---

### Post by squaby on 2009-08-24
Hello all!

I seem to be experiencing the same problem as...sorry, don't remember the name in the first post.
I've been trying to connect to both my msn and gmail accounts but I never manage to get online. A "network error" constantly appears afterwards. 
At first I thought it was a problem with the internet provider (reaaaallllly slow downloads, probably incapable of downloading these chat rooms or whatever they are called) but now I'm using a better connection and the problem remains. 
I've already tested both accounts, through the gmail and msn separately, and they work fine. 
I've tried uninstalling and reinstalling the pidgin but no further enlightenment was provided through this brilliant idea (great idea, indeed!). I've also installed Empathy (though it might have been a pidgin update problem, which, buy the way, has also been updated as far as I can tell) but the problem lingers (what are the odds?!)
As i'm not an expert (at all) I am really running out of options. Does any one have a clue what's happened? It worked fine the first time I used it...(a couple of months ago).

Whatever the suggestions are, please make it gentle. I'm not a computer genius...:P

Thanks!

---

### Post by jesuisbenjamin on 2009-08-24
it does support msn i am using it at the moment.

---

### Post by DFlame on 2009-08-25
I am also connecting without any trouble. Lets try getting a debug output.

Ensure Pidgin isn't running, then open a clean Terminal window and issue this command:

```
pidgin -d &> crash.txt
```

This will print debugging information to a file called crash.txt in your home folder. After the crash occurs, open the file and remove any personal information that might be found (contact email addresses etc).

If the log is huge, use a service like [Pastebin](http://www.pastebin.com) to upload it, then post the link here. If it's not that big, just post here :)

This might give us some clues as to where exactly it goes wrong

---

### Post by cguy on 2009-08-25
Pidgin is version 2.6.1. Try it out!

---

### Post by Tibuda on 2009-08-25
> **cguy said:**
> Pidgin is version 2.6.1. Try it out!

Instructions to update Pidgin in [http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)

---

### Post by XicoXperto on 2009-08-25
after i made the update 
> 
[QUOTE]Quote:
Originally Posted by cguy View Post
Pidgin is version 2.6.1. Try it out!
Instructions to update Pidgin in [http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)[/QUOTE]

its working now.
Ty everybody

---

