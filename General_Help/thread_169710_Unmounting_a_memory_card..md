---
title: "Unmounting a memory card."
date: 2006-05-03
forum: General Help
---

### Post by xmastree on 2006-05-03
I'm sure this has been discussed, and I've seen people say they just unplug them. But...
This has happened twice to me now.

I had taken some pictures, and the card was in the reader. I left it there while my daughter logged in to another x session.

While she was logged in, I took the card and put it in the camera to take more pics.

I then switched back to my login and replaced the card (which was still visible on the desktop). The new pictures didn't show, so I unmounted and remounted it. Now I don't have permission, only my daughter, so I flipped over to her login and unmounted it. Logged her off, back to me, plugged in the card and the new pictures weren't there.

I put the card back in the camera, and they didn't show there either. Luckily they were nothing I couldn't take again.

The moral is, **unmount the card**

---

### Post by loell on 2006-05-03
I've had similar expiriences too with my cellphone's mmc..

---

### Post by dotdot on 2006-05-03
i agree - umount the card.

if any one here says other wise - come on give us  small explanation.

YOU CAN'T DO IT simply because the detail you were writing may not have been flushed to disk / mem.

If you haul it out - you may trash the card - (in this case).

Manual umount - ..... should work.

Next time you plug it in it should  mount up no problem.

..be careful people....

..

---

### Post by towsonu2003 on 2006-05-03
I always check mounted places (even after I umount the memory card or flash drive or whatever peripheral) so I don't screw it
```

mount
```
the name of your device (name for flash drive would be /dev/sda1 or such) shouldn't be in the output. 

I saw flash drives trashed after just unplugging. filesystems and/or partition tabels screwed... needing a format... so: umount your thing and make sure it is umounted :)

---

### Post by xmastree on 2006-05-03
[QUOTE=dotdot]YOU CAN'T DO IT simply because the detail you were writing may not have been flushed to disk / mem.[/QUOTE]I wasn't writing to the card though. Only reading. The pictures which were on it when I first plugged it in were intact, it was the ones I took after I pulled it which disappeared. I thought the system may have taken a 'snapshot' of it when I first mounted it, which is why I tried unmounting and remounting it.

Didn't work though.

---

### Post by towsonu2003 on 2006-05-03
[QUOTE=xmastree]I wasn't writing to the card though. Only reading. The pictures which were on it when I first plugged it in were intact, it was the ones I took after I pulled it which disappeared. I thought the system may have taken a 'snapshot' of it when I first mounted it, which is why I tried unmounting and remounting it.

Didn't work though.[/QUOTE]
there is a chance the filesystem got corrupted when you took the thing off. that happened to me once (not with newly written data though). I took the thing off, put it to windows, went to a folder in it, and it was emptied... tried to put something in the folder, and windows told me "this thing is screwed", so I reformatted. 

maybe the filesystem got corrupted, camera tried to write to that corrupted part, couldn't write but didn't give any errors, so you thought everything was ok... can you see the new pictures in a windows computer? (if you can, I'm clueless)

and if you decide to format, format it using the camera's utility (i.e. tell the camera to format it), not Linux or Windows utilities.

---

### Post by bluenova on 2006-05-03
Always unmount flash cards. I even advise my friends who use windows to to do the 'Stop device' before removing it, as most just pull it out.

---

### Post by towsonu2003 on 2006-05-03
[QUOTE=bluenova]I even advise my friends who use windows to to do the 'Stop device' before removing it, as most just pull it out.[/QUOTE]
that's good advice, because windows is not different from Linux in mounting. It's just more GUI'd. when you eject a Cd, it is first unmounted. The "Stop the device" also means "unmount it" (although I think it also cuts power to the device, which is different from what Linux does).

---

### Post by xmastree on 2006-05-03
[QUOTE=towsonu2003]maybe the filesystem got corrupted, camera tried to write to that corrupted part, couldn't write but didn't give any errors, so you thought everything was ok... can you see the new pictures in a windows computer?[/QUOTE]I reviewed the pictures in the camera, so I'm sure they were onthe card. As for Windows, I didn't try, I just took the pics again. No need to reformat the card, and the older photos were still there. It was as if i hadn't taken the other ones at all. :-k

---

