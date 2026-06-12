---
title: "Chrooting users to their own home/system folder"
date: 2006-05-25
forum: General Help
---

### Post by rambash on 2006-05-25
First, I'm quite a newbie when it comes to Linux. So please bear with me :).

I was looking for a way to jail users to their own home folder, or better, simulating a system. So I looked into jailing/chrooting hoping to find a quick solution but, offcourse, there was none. ](*,) 

I started experimenting and I quickly understood that when using the chroot command you need certain files. (binaries?)
So i built up my new "system" with the files named in the G.2 chapter at this [page]("http://www.debian.org/doc/manuals/securing-debian-howto/ap-chroot-ssh-env.en.html").

I created a new user, "testuser", and I let his home directory be /home/vroot/home/Guest. The fake system I had created is located at vroot. So it's vroot/bin, vroot/etc and so on. 

I then added the "testuser" to the admin group in the /etc/group. So that "testuser" would be able to use the *sudo* comand.
```

admin:x:106:regularuser, testuser
```

I could now connect to my server with SSH using testuser and then use chroot /home/vroot/. But having the user chrooting vroot all the time doesn't really get me closer to my goal ;)

If only a command could be run every time someone connected with SSH, right?
So I read up on *bash* and I saw that .bash_profile could be used for this. 
I added these lines at the bottom of .bash_profile: (located at /home/vroot/home/Guest/)
```
sudo chroot /home/vroot
cd /home/vroot/home/Guest/

```

And voila, It works! Now on to the question! :)

Why is this method not used by others? I do realize that adding the user to the admin group might be a security risk. But can't the selection of commands be controlled, since we are using our own root?

In any case, I'm happy to have done this. It gave me a lot of knowledge about the system. I'm not familiar with the ways of ubuntuforum but I'll just say it anyway: Please dont flame me for being stupid 8)

Rambash

**Edit:** Maby this thread should be moved to Server talks? Sorry about that ;)

---

