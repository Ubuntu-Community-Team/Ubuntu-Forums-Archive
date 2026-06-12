---
title: "Problem with system crashing"
date: 2011-08-01
forum: General Help
---

### Post by shmalphy on 2011-08-01
I have been having a problem since I installed the Wubi version of Ubuntu. My screen goes white occasionally, and the system becomes unresponsive. Also, sometimes the launcher doesn't load correctly and I have to restart, which is now taking forever.

I am getting low disk space warnings, and I am thinking of eliminating Vista from my computer, but I want to work out the bugs first. I am not sure if it's the case, but I suspect having both OS's on the hard drive is the problem, not leaving enough space. Any thoughts on the system crash or how to speed up my start up time?

---

### Post by Mark Phelps on 2011-08-01
The simple fact of having two OSs installed on the same drive is not going to, in and of itself, lead to instability of any kind.

You're most probably getting low disk space warnings (in Ubuntu, I presume) because you likely let Wubi install to the minimum space -- which is too small once you start using it a lot.

That said, if you're having stability problems in Ubuntu, the fact that you installed it using Wubi doesn't really mean anything.  While the file resides inside an NTFS partition, Ubuntu is really running by itself.

You will encounter the same problems if you install it inside its own Ext4 partition.

---

### Post by shmalphy on 2011-08-02
Thanks for the response, but it doesn't really solve my issue. 

I looked, and Windows is using 20% of my hard drive. I was hoping that removing an application that large would free up space and make my computer faster and more stable. I didn't really understand that Ubuntu was only being given a certain amount of space on my hard drive, that would make sense. I am a rank newb so please feel free to explain this to me as if your speaking to a 3 year old.

The problem has gotten progressively worse, to the point where I can no longer even get Ubuntu to start. When I say it was "crashing" I mean that when i didn't press anything for awhile it would go into power saver mode, and the music would still be playing, but the screen would go white, and it would not pop up with the expected option to enter my password. Now when I start up, it asks for my password at a different looking log in screen, then goes blank then asks for the password again. It won't log in at all. Does anyone know what might be causing this to happen? 

It is also repeatedly getting stuck at the initial startup screen when I turn the computer on (where it gives the option for system recovery etc) and shutting down right away. It won't let me run system recovery, or respond at all. For awhile I thought I destroyed the computer...

I really like Ubuntu, and want to make it work, but I had to go back to Windows just to type this, so I am scared to take the plunge just yet. I am not sure if the problem is that my machine can't handle the load, or the settings are wrong and I should give Ubuntu more space, or maybe something else. Please help me figure this out, I am going insane!

---

