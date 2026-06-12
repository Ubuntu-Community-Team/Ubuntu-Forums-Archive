---
title: "Can't get aliases working in profile files (?)"
date: 2006-04-11
forum: General Help
---

### Post by TomG on 2006-04-11
Hi

I cant get aliases working in Ubuntu. Eg :
I create a simple alias="ls -l" in the .bash_profile and then logout and reconnect -> does not work.
If I do a '. .bash_profile' it works.

If I create the alias in /etc/profile it does not work when logging via splash screen but works with a new connection via a 'su -'.

Splash screen connections do not use any profile files ?

What's wrong ?
Tx
Tom

---

### Post by WakkiTabakki on 2006-04-11
Yes, please! If anyone know how to make sense of this, please let us know.

Thing is, apparently the .bash_profile sits unused... 
I added this to the end of my .bashrc (essentially executes the .bash_profile if it exists)
```

if [ -f ~/.bash_profile ]; then
  . ~/.bash_profile
fi

```

And, don't forget! Check your .bash_profile for any code that tries to execute the .bashrc (or else they'll keep running eachother 'til the penguins come home!)

What I can't make any sense of is that there is a .bash_profile, but it won't automatically get run... Why? 

Good luck
/N

---

### Post by xenmax on 2006-04-11
Refer these thread:
[http://www.ubuntuforums.org/showthread.php?t=81747](http://www.ubuntuforums.org/showthread.php?t=81747)
which also quoted in 
[http://www.ubuntuforums.org/showthread.php?t=152722](http://www.ubuntuforums.org/showthread.php?t=152722)

---

### Post by TomG on 2006-04-11
Thanks guys. 1st thread with gnome-terminal setting works perfectly. Just think that it could be set by default :)

---

