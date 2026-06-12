---
title: "Citrix Terminates when doing remote on users"
date: 2012-02-29
forum: General Help
---

### Post by Pidi on 2012-02-29
Hello

Reinstalled my computer 2 months ago to Ubuntu 11.10 from Windows XP.
The purpose of this was to learn more about Linux.

The main goal was to make my computer able to remote users true Citrix Client.
So that I could still support people with help at work (IT-Apprentice).

Everything works like a charm except when I'm going to remote a user.
Citrix terminates itself after the user has confirmed the remote help.

How it should work:
After the user has confirmed the remote help, my session is hidden / minimized and then the users session opens. 
From there both can see and use the computer. 
When the problem / issue is solved, the user presses a key combination to stop the remote and my session is restored.

Things I've tryed:
- Made myself as owner of all ICAClient / Citrix Files
- Chmod 755
- Chmod 777
- Run it as root

Best Regards
Pidi


Edit:
After some hours of testing I've discovered that the termination of my sessions was caused by to high color mode.
When I was using 24bit Color Mode, I could only remote other users with 24bit Color Mode, which gave me termination of my session when I tryed to remote 16bit / 32 Thousand Color mode users.
The solution was to lower my Color Mode from 24bit to 32 Thousand. This gave me access to remote users with 32 Thousand -> 24bit Color Mode. Little Odd but works like a charm!

Admin's can now close this thread.

---

