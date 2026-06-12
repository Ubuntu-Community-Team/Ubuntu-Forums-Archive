---
title: "Howto: Midi With AC97 Audio"
date: 2006-04-07
forum: General Help
---

### Post by mauriciorossi on 2006-04-07
This is my first how-to so be patient with me ;)
To get midi with ac 97 audio all you have to do is the following:
Go to the terminal and type
```

apt-get install timidity

```
then go to system->preferences->sessions then ad the folowing line to startup programs
```

timidity -iA -B2,8 -Os1l -s 44100 

```
now use whatever midi program you want but choose port 0 and it should work 8)

i have only tested this with noteedit, kmid, and pmidi, but i think it should work on others too 8)

---

### Post by mauriciorossi on 2006-04-07
sorry, i thought i was under how-to's, can a mod please move it there? ;)

---

### Post by Carcass on 2007-03-10
I have this error > timidity -iA -B2,8 -Os1l -s 44100
/etc/timidity/freepats.cfg: No such file or directory
timidity: Can't read any configuration file.
Please check /etc/timidity/timidity.cfg

I have no sound already??? :(  

help me to play sound in kmid please

---

### Post by Carcass on 2007-03-10
any idea ?

---

### Post by dragonriot on 2007-03-24
> **Carcass said:**
> I have this error 

I have no sound already??? :(  

help me to play sound in kmid please

Yeah... install "freepats" with timidity

---

### Post by Carcass on 2007-03-26
Thanks

I tell you soon .........:)

---

### Post by jonnylinuxnerd on 2007-04-02
This guide worked great for me!
Thanks :)

---

