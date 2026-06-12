---
title: "why does &quot;root&quot; have control and not me?"
date: 2009-11-24
forum: General Help
---

### Post by zarf on 2009-11-24
I am trying to get an understanding of why I as admin cannot do things which are owned by some demented demon named "root"?;)

for an example (and there are many) I cannot delete files piling up in my bootchart log. I cannot drag the files to trash and the "move to trash" in the dialogue box is greyed out.

is there a fairly simple reason for root having such control? Is there a permanent way around?

thanks

---

### Post by Kareeser on 2009-11-24
The root, or superuser, account, protects you from yourself.

You are an administrator, yes, but you still do not have complete control, just in case your account gets compromised.

You can act as root using the "sudo" command, or "gksudo" for graphical applications.

```
i.e. gksudo nautilus
```

---

### Post by lisati on 2009-11-24
Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by shaggy999 on 2009-11-24
Ok, this analogy may be a bit weird, but bear with me.

The root user is kind of like 'god'. Your user is kind of like an archbishop or something who 'talks' to god and can make requests through the 'sudo' command. So the files you are trying to delete belong to this god user and by requiring you to make that request you minimize the chances of completely destroying your system. It's also great for auditing because you can see which users executed administrative tasks.

In order to delete the files in question you need to do one of two things:

1) Claim control over the files and then delete them as your user.
2) Request 'god' to delete them.

For step 1 use the 'chown command' to take ownership of the files. Then delete.
For step 2 just execute the delete command with 'sudo' in front and type in your password when requested.

It's highly recommended that you not try to disable the mechanisms put in place. They are there after 20-30+ years of UNIX refinement and the mechanisms work extremely well to ensure secure and smooth-running systems.

---

### Post by zarf on 2009-11-25
Thanks all for the quick replies. I'll certainly look up the links suggested, and yes, the 'weird' analogy does make sense.

 I can see its going to take a leap to get out of the *windows* frame of mind.

---

### Post by jacobs444 on 2009-11-25
Yes, unless specifically changed in windows, you are always running around with true Admin privelages, this is why malware does so much damage on windows.

---

