---
title: "Sync solution for 11.04? Looking for Unison/LuckyBackup help."
date: 2011-09-22
forum: General Help
---

### Post by dkh3184 on 2011-09-22
New user, getting really frustrated. I have having a really hard time getting any sync application to work properly. 

I have a desktop and a netbook and want to since the personal folders (Documents, Pictures, etc.) between the two. Both machines are running Ubuntu 11.04, both machines have the same login and password (probably a bad idea). I have managed to get openssh to work (password only, haven't got keys working yet) and can log in to the remote machine (either).

I have tried to use Unison, but there is a password bug. It doesn't seem very clear if this has been fixed or what the current status is. I have seen messages that indicate that it is fixed and some that say it isn't.

I have tried LuckyBackup. I actually managed to get it to work, briefly, but it keeps freezing and then I get an error:   p, li { white-space: pre-wrap; }[COLOR=#ff0000]r[/COLOR][COLOR=#ff0000]sync: connection unexpectedly closed [COLOR=Black]The only way I have found to fix it at that point is to restart both machines. But then it just does it again.

Frustrated, I have even tried to do it manually. But other than ssh through the terminal, I can´t get the two machines to see each other. 

I really need to get one of the sync programs (LuckyBackup preferably since I have actually had some success with it, sort of, but it really doesn't matter) working. If I cannot sync between the two, it is a deal breaker as far as Ubuntu and I are concerned (and other than this issue I am really pleased with Ubuntu).

Dáire
[/COLOR][/COLOR]

---

### Post by dkh3184 on 2011-09-22
Okay, just tried it with just rsync and it still hangs. Lovely. If it is an rsync issue I assume that it will affect any program I hope to use for syncing.

Dáire

---

### Post by dkh3184 on 2011-09-22
Pretty poor solution, but apparently rsync sends and incremented list of the last files synced. So, I can run it over and over until I actually get through all the files. Ugly, but I'll at least have a backup of the files on the netbook.

Anyone have any ideas about why it's hanging?

Dáire

---

### Post by papibe on 2011-09-22
Welcome to the forums!

My guess both Unison and rsync are failing for the same reason. How are the machines connected to your router? Are any of them wireless?

Regards.

---

### Post by dkh3184 on 2011-09-22
Yes. The netbook is wireless.

Unison's failure is a bug. The ssh connection is not asking for a password. Just sits there waiting for it forever, but doesn't prompt for it.

Dáire

---

### Post by papibe on 2011-09-22
My first guess was a weak or unstable wireless connection, but that change things a little bit.

How far did you go trying to set public keys?

Regards.

Edit: rsync works over ssh by default, so if that is not working properly it could be the source of problems. Try reseting any keys by deleting the directory ~/.ssh/ on both machines. Then try to ssh normally (the first time may you'll be greed by an ugly long message).

Edit2: in the meantime, add the option --partial to your rsync commands so partial transfers are kept, and not started from scratch if the connections fails (very useful for big files).

---

### Post by dkh3184 on 2011-09-24
I don't think it's the wireless since I never had an issue syncing under Windows. 

I did manage to get Unison to work, from the netbook anyway, although I'm not entirely sure how. And of course it hangs just like the rest do.

Still trying to get ssh keys figured out. Once I generate the key pair, key_name is the private and key_name.pub is the public? What folders do they need to be placed in on the machines?

Dáire

---

### Post by dkh3184 on 2011-09-24
And it was the wireless after all. Apparently, Ubuntu doesn't care for my wireless for some  reason. Connecting it with a cable solved the problem. +1 for Windows I  guess. Weird.

Dáire

---

### Post by papibe on 2011-09-24
I would advice you to search the forums for some fixes related to your wireless card (get your brand and model). There's some proprietary drivers/updates that improve or fix several wireless problems (not available on the software center).

You could even create a new thread to tackle this particular problem.

Regards.

---

### Post by bpb_21 on 2011-09-24
> **dkh3184 said:**
> And it was the wireless after all. Apparently, Ubuntu doesn't care for my wireless for some  reason. Connecting it with a cable solved the problem. +1 for Windows I  guess. Weird.

Dáire

I just wanted to mention I have the same problem with rsync/luckybackup over wireless. I get that same error message but only on files over approximately 300 or so MB. I'm using SSH from my laptop to a server also running 11.04.

Here's the really strange part: I can copy a gigabyte or larger sized file over wireless just fine to the server. But, using rsync/luckybackup it gives me that same error message every time, unless I use a wired connection.

Not sure why I would be able to copy large files fine wirelessly but not rsync them wirelessly.

---

