---
title: "Changing uid of existing user"
date: 2010-06-14
forum: General Help
---

### Post by John Bean on 2010-06-14
I have a Lucid installation with one user (johnb - me!) which was of course given the default UID of 1000. For reasons I won't bore you with I'd like to change this to a different number, 1003 say. I won't be changing anything else.

Now I've done this in the past with non-gui *nix systems using usermod from a root login but I'm a bit wary of doing this with Lucid for all sorts of reasons, primarily of course the whole X system and GNOME. I'd rather put up with the inconvenience of leaving it alone than risk breakages by changing it.

Anyone got experience of using usermod on a modern Ubuntu system? If so, is there a safe way to use it without a root login?

---

### Post by CharlesA on 2010-06-14
You could probably do it, but it would more than likely break a bunch of stuff.

Why not just create a new user with a specific UID?

If you are worried about the NAS, they go off the username not the UID when connecting to it.

---

### Post by gmargo on 2010-06-14
I believe it is safe to do, and you won't break anything.  However, you have already recognized the problem in case a mistake is made (or my bold claim is wrong!).  So it would be foolish to proceed without creating a root login or at least another userid with root privileges.  And when you do it, you should not do it with a series of sudo commands, but use 'sudo bash' and do it from a root shell.

And you can always create a new user just to experiment on, before you mess with your own.

---

### Post by John Bean on 2010-06-14
> **CharlesA said:**
> If you are worried about the NAS, they go off the username not the UID when connecting to it.

Ah, you must have read my post before I edited out the NAS bit (I thought I'd deleted it before posting but I left some text in).

But now you mention it, the minor irritation is indeed the NAS, a rather nice Netgear SPARC based box running a form of Debian. I bought it because of the simplicity of use as out of the box it supports CIFS (for my XP netbook), NFS (for my Ubuntu box) and Rsync which I use from both, along with assorted media streaming protocols and of course HTTP(S) and FTP. Being a Linux box it of course uses UID/GID to define file ownership, and although I can map this to any *local* user I can't use 1000 because that UID is already used by user "backup".

What this means in practice is that transparency between the CIFS and NFS views of file ownership is lost - files saved over NFS from my Ubuntu box are inaccessible to the CIFS connection to the netbook until I chown them to be other than user 1000; I think something in the NAS treats files owned by user 1000 in a special way.

I could meddle with the NAS to map NFS connection UIDs but I'd rather not - there are no options to do it in the web-based configuration. I can and have created a new user on the NAS and the lowest UID it allows me to use is 1003, so the obvious solution is to change my Ubuntu UID to match.

Maybe I'll just live with the irritation...

---

### Post by John Bean on 2010-06-14
> **gmargo said:**
> And you can always create a new user just to experiment on, before you mess with your own.

I'm becoming less inclined to experiment the longer I think about it.

Thanks for the suggestions though :-)

---

### Post by ububaba on 2010-06-14
I have hard disks which have different login names that creates problems 
at times. For a smoother running now want to have the same login name
on all of them. What would be the most painless operation? 
Thanks for your suggestions.

---

