---
title: "I messed up my X11....I think"
date: 2009-07-25
forum: General Help
---

### Post by ironhorse99 on 2009-07-25
I was running 9.04 with a Nvidia Gforce 6200-a with 256 memory and wanted to run Picassa which installed but when I tried to run it I got a box saying I needed to run a command something like "chmod 666 nvidia/ct1" or something like that. It wouldn't accept this command untill I altered it. Now its broke, won't start. I've had some help in uninstalling all the nvidia stuff but it won't start. Can someone help me with the xorg.config so I can get back into the system. If I can at least load a generic video driver I may be able to reconstruct the config file as I have notes that I can't get to. I know this is a big mess but "I PROMISE" I'm never doing anything like that again. Mike

---

### Post by madsmeg on 2009-07-26
Never make such promises, half the fun of breaking a system is fixing it and learning more about what you are doing.

```
sudo dpkg-reconfigure xserver-xorg
```

This should be able to help you through...

Let us know how it goes

---

### Post by ironhorse99 on 2009-07-26
> **madsmeg said:**
> Never make such promises, half the fun of breaking a system is fixing it and learning more about what you are doing.

```
sudo dpkg-reconfigure xserver-xorg
```

This should be able to help you through...

Let us know how it goes

Thanks, I'll give it a try & get back.
I'm a little bummed as I hav been learning a little here & there but failed to make paper copies.....now things are where I can't get to them.

---

### Post by Bucky Ball on 2009-07-26
Wild guess? You changed permissions for something Nvidia so Piccassa could access the card which might have stuffed things. Removing Nvidia stuff, xorg.conf now boots with the instructions to use your nvidia driver which is no longer there. That is what you need to change.

The instruction posted by madsmeg should get you going. Break away, just back things up before you smash them! Once you have a solid xorg.conf again, copy it and then try again. Remember: The working xorg.conf you have backed up will be useless if it uses nvidia and the driver is not there so sometimes an idea to keep a 'vanilla' version and an 'nv' tweaked version. :)

---

### Post by ironhorse99 on 2009-07-26
> **madsmeg said:**
> Never make such promises, half the fun of breaking a system is fixing it and learning more about what you are doing.

```
sudo dpkg-reconfigure xserver-xorg
```

This should be able to help you through...

Let us know how it goes

That didn't work, it still drops me to a dos style login screen & when I login with correct username/password it returns with the same login screen. What now......

Here's a link to another help site where I go through the whole scenario. Perhaps this will give additional info in helping solve this problem. [[https://answers.launchpad.net/ubuntu/+question/76860]](https://answers.launchpad.net/ubuntu/+question/76860])
One additional note: I have split the drive into 2 partitions without destroying the original Operating System. I upgraded ver.8 to 9.04. I could, if I knew how, copy what I need to get the original system back. One problem is I can't access the partition....seems odd but then again I don't know much.

---

### Post by Bucky Ball on 2009-07-27
When you get to that login screen and have logged in, try

```
startx
```

---

### Post by ironhorse99 on 2009-07-27
> **Bucky Ball said:**
> When you get to that login screen and have logged in, try

```
startx
```

That's just it, I can't login. Each time I do it returns asking me the same questions, ie, login,followed by password, over and over. It doesn't say their wrong,just keeps asking.

---

### Post by Bucky Ball on 2009-07-27
Do you get a grub menu at boot and if so can you select recovery mode? If there is no grub menu, try hitting escape repeatedly after post and before it gets to grub or login or whatever.

---

### Post by ironhorse99 on 2009-07-27
I do get the grub & run recovery mode.

---

