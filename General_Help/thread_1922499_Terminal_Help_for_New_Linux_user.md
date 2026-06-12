---
title: "Terminal Help for New Linux user"
date: 2012-02-08
forum: General Help
---

### Post by JordanCrr on 2012-02-08
Hey guys. I've just started using Ubuntu for the first  time about a week ago (it's the first Linux Distro I've ever used) and I LOVE it! I'm catching on really quick, but I'll get to the point rather than boring you all.

I've been trying to familiarise myself with the Terminal. Whether it be commands or navigating it, etc. But one thing I haven't been able to figure out is how to enter a directory's title if it has a space in it. I know this may be rudimentary to some of you folks, but I just can't figure it out. And I know I'm probably gonna kick myself when I figure it out.
Oh well.
I love Linux and I love the community here!
Thanks everyone! :)

---

### Post by papibe on 2012-02-08
You can use quotes:
```
cd 'My Music'
```
or escape the spaces with a '\':
```
cd My\ Music
```
Hope it helps.
Regards.

---

### Post by Rafterman414 on 2012-02-08
You can try to enter the directory name in quotes or you can put \ in after the word and before the space, for example:

```
cd /home/user/a\ folder/things
```

papibe beat me to it, but yep thats how its done.

---

### Post by JordanCrr on 2012-02-08
Thanks so much for the quick response you guys! Thanks for the great help :)

---

### Post by jwbrase on 2012-02-09
Also, you can often get by with not typing a command or filename out completely. [Tab completion]("http://en.wikipedia.org/wiki/Tab_completion") is your friend.

---

### Post by drmrgd on 2012-02-09
> **jwbrase said:**
> Also, you can often get by with not typing a command or filename out completely. [Tab completion]("http://en.wikipedia.org/wiki/Tab_completion") is your friend.

+1
Use tab completion whenever possible.  This will help you when you have things like spaces in file / directory names (which you should try to avoid anyway), help save you some typing time, and (and I think this is the most useful feature) prevent you from having commands fail due to typos - especially in the case of really long file names.

---

### Post by Rafterman414 on 2012-02-09
> **Major_Bloodnok said:**
> Just don't use spaces with linux file names and directories, PERIOD.
Use underscore "_", or dash "-" instead, i.e. My_Music.

I agree I try to avoid spaces whenever possible but sometimes if you dual boot and are messing around with partitions that have files from Windows you have to deal with spaces.

---

### Post by killfall on 2012-02-09
One other tip could be that if you are still getting used to linux and you want to get to a specific folder to perform a certain action but the folder is quite deep in a file system and you dont want to have to cd all the way into it then you can install an extention to nautilus so you can navigate to that folder right-click and then click 'open terminal here'.
 
Install instructions here [http://ubuntuforums.org/showthread.php?t=104408](http://ubuntuforums.org/showthread.php?t=104408)

---

