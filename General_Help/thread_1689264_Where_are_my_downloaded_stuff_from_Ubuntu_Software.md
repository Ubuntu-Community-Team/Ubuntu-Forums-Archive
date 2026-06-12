---
title: "Where are my downloaded stuff from Ubuntu Software center?"
date: 2011-02-16
forum: General Help
---

### Post by speedruntrainer on 2011-02-16
Hello.

I'm very new to Ubuntu.

I just downloaded MupenPlus emulator with Ubuntu Software Center, I know I can open it with Applications > Games > Mupen64plus. But that's not the problem.

I know how to change plugins, but I want other plugins.
So where is the Mupen64Plus folder?
I looked at my home folder and other folders but it isn't there :S
Where can I find it?

Thanks.

---

### Post by kn0w-b1nary on 2011-02-16
you have to first run the program, then second, select to view hidden files.

Hope this helps!

---

### Post by wormyblackburny on 2011-02-16
more than likely in /opt or /etc.....

try **sudo apt-file list packagename**, that will list all the files installed when you installed the package

---

### Post by 3Miro on 2011-02-16
All program in Ubuntu are split into many small packages. The best way to view the details of individual packages is to use Synaptic Package Manager (System -> Admin -> Synaptic).

Most things are installed in /ust /opt /usr/something places. However, individual settings for each program are in /home/your_name/.something To see the hidden files (those starting with .) open Places -> Home and then hit Ctr + H. (be careful with those as you can mess important settings)

---

### Post by speedruntrainer on 2011-02-16
Ok, did that, looked it and I don't see a Mupen64Plus folder omg.
I see some for feux but I don't need feux atm, I need Mupen.

---

### Post by oldos2er on 2011-02-16
[http://code.google.com/p/mupen64plus/wiki/FileLocations](http://code.google.com/p/mupen64plus/wiki/FileLocations)

---

### Post by speedruntrainer on 2011-02-16
Thanks, I copied the plugins I got from other N64 emulator I have for Windows, to there, but I can't choose others when I want to change them.
I mean, in Mupen64Plus, you go to options > configure, Graphics plugin, input etc.
But I just see the plugins I had, not new ones.
The plugins I want to use are dll files, is that the problem?

The plugins I'd like to use are:

Graphics: Jabo's Direct3D8 1.6
Controller: N-rage's Direct-input V2 1.80a
Sound: Jabo's DirectSound 1.6

But I don't see them.

Is it even possible to use it with Ubuntu???

---

