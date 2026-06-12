---
title: "Sudoer"
date: 2011-04-12
forum: General Help
---

### Post by shashanksingh on 2011-04-12
I want my user to be in the default sudoer's list so that I dont have to type sudo all the time.

In the passwd file, I changed my userid to 0 which is the default root id, but it caused some problems.
Any more simpler and problem free method to do it???

---

### Post by CharlesA on 2011-04-12
You can edit /etc/sudoers but you'll still have to type "sudo"

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by shashanksingh on 2011-04-12
> **CharlesA said:**
> You can edit /etc/sudoers but you'll still have to type "sudo"

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

No turnaround to that???

---

### Post by CharlesA on 2011-04-12
Not unless you want to login as root all the time, which you really shouldn't do.

---

### Post by earthpigg on 2011-04-12
we really aren't normally supposed to share this, but because you are specifically asking:

```
sudo -i
```

there, you are logged in as root in that terminal. if you keep that terminal open, you can run commands as root all day without typing sudo. until you mistype something and break your system, that is. :)

i suggest you edit /root/.bashrc and/or ~/.bashrc so that when logged in as root, the color scheme is significantly different. to prevent you from not noticing the # and running something as root that you intended to run as yourself.

edit: see attached. they look very different, so awareness of root is nearly earthpigg proof.

edit2: replaced "sudo su" with "sudo -i"

---

### Post by CharlesA on 2011-04-12
The preferred way is using sudo -i IIRC.

---

### Post by CharlesA on 2011-04-12
The preferred way is using sudo -i IIRC.

---

### Post by earthpigg on 2011-04-12
out of curiosity, is there a difference besides starting in root's ~?

---

### Post by CharlesA on 2011-04-12
Different $PATH I think. Not sure.

---

### Post by Rasa1111 on 2011-04-12
I'd much rather have to type 4 little characters than risk everything that could go wrong by doing what you want.

Choose your poison, I guess. 

Is typing "sudo" *really* that much of an inconvenience? 
:o

---

### Post by earthpigg on 2011-04-12
i wonder how much would be broken by this:

(don't actually type this, please. it is a question, not a suggestion.)
```
sudo mv /usr/bin/sudo /usr/bin/s
```

now, only 1 letter would be required -- assuming that doesn't break the entire system.

---

### Post by mcduck on 2011-04-12
> **earthpigg said:**
> out of curiosity, is there a difference besides starting in root's ~?

Yes, there definitely is. You'll also be using root's configuration files and environment variables instead of your user's config files and variables. So it avoids the annoying possibility of some comamnd you run changing the ownership of your normal user's files.

In other words, "sudo -i" behaves as if you'd actually logged in as root, while "sudo su" (at least to some extent) behaves like you are still your normal user, only with root's permissions. The latter can of course cause all kinds of problems.

---

### Post by yetiman64 on 2011-04-12
> **mcduck said:**
> Yes, there definitely is. You'll also be using root's configuration files and environment variables instead of your user's config files and variables. So it avoids the annoying possibility of some comamnd you run changing the ownership of your normal user's files.

In other words, "sudo -i" behaves as if you'd actually logged in as root, while "sudo su" (at least to some extent) behaves like you are still your normal user, only with root's permissions. The latter can of course cause all kinds of problems.

+1, check out the summary table in [--this link--]("http://ubuntuforums.org/showpost.php?p=6188826&postcount=4") for a good comparison of sudo commands.

"sudo -i" is advisable for root terminal usage.

---

### Post by Spyderkid on 2011-04-12
Don't login as root all the time!

whats the big deal its only 4 letters?

---

### Post by shashanksingh on 2011-04-12
> **earthpigg said:**
> we really aren't normally supposed to share this, but because you are specifically asking:

```
sudo su
```

there, you are logged in as root in that terminal. if you keep that terminal open, you can run commands as root all day without typing sudo. until you mistype something and break your system, that is. :)

i suggest you edit /root/.bashrc and/or ~/.bashrc so that when logged in as root, the color scheme is significantly different. to prevent you from not noticing the # and running something as root that you intended to run as yourself.

edit: see attached. they look very different, so awareness of root is nearly earthpigg proof.

Thank you, this was helpful. About typing the four letter word, I understand why it is so, just thought of tweaking a way out of it if possible..

Thanks ppl

---

