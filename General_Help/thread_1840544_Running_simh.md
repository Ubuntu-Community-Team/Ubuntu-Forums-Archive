---
title: "Running simh?"
date: 2011-09-07
forum: General Help
---

### Post by bogdarnet on 2011-09-07
Installed simh from the repositories, but I can't figure out how to run it...

---

### Post by haqking on 2011-09-07
> **bogdarnet said:**
> Installed simh from the repositories, but I can't figure out how to run it...

Dont you have to manually build each emulator you want to run then once thats done launch it with something like

/usr/local/vax/bin/vax

which starts the emulator then install VMS in this case

its been a while, you used to be able to get the documentaion from trailing edge ?

EDIT: ahh yeah here you go [http://simh.trailing-edge.com/](http://simh.trailing-edge.com/)

it has all the documentation

---

### Post by jwbrase on 2011-09-07
> **haqking said:**
> Dont you have to manually build each emulator you want to run then once thats done launch it with something like

Not with the packages in the Ubuntu repositories. All the emulators come with ready-to-run binaries.

@OP: The first point of confusion you may be running into is that SimH isn't just one program. So instead of running "simh" you have to run the appropriate emulator for the machine you're trying to emulate. E.g, to run the PDP-11 emulator, you need to type:

```
pdp11
```

Beyond that, I need to know what exact problem you're running into. Are you trying to run specific software on one of the emulators and having trouble with it?

Also, /usr/share/doc/simh contains a bunch of documentation that may be helpful.

---

### Post by bogdarnet on 2011-09-08
> **jwbrase said:**
> Not with the packages in the Ubuntu repositories. All the emulators come with ready-to-run binaries.

@OP: The first point of confusion you may be running into is that SimH isn't just one program. So instead of running "simh" you have to run the appropriate emulator for the machine you're trying to emulate. E.g, to run the PDP-11 emulator, you need to type:

```
pdp11
```

Beyond that, I need to know what exact problem you're running into. Are you trying to run specific software on one of the emulators and having trouble with it?

Also, /usr/share/doc/simh contains a bunch of documentation that may be helpful.

Thanks!  This is very helpful... I was trying 'simh' which clearly didn't work... 'pdp11' gets me a prompt, and I'll be looking at the /usr/share/doc/simh files as well.

---

### Post by haqking on 2011-09-08
> **jwbrase said:**
> Not with the packages in the Ubuntu repositories. All the emulators come with ready-to-run binaries.

@OP: The first point of confusion you may be running into is that SimH isn't just one program. So instead of running "simh" you have to run the appropriate emulator for the machine you're trying to emulate. E.g, to run the PDP-11 emulator, you need to type:

```
pdp11
```Beyond that, I need to know what exact problem you're running into. Are you trying to run specific software on one of the emulators and having trouble with it?

Also, /usr/share/doc/simh contains a bunch of documentation that may be helpful.


ha gotcha ok, wasnt familiar with the one from the repos, i was reaching backinto brain from manual install.

good heads up

cheers

---

