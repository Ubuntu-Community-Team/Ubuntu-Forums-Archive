---
title: "How to look at crash logs?"
date: 2009-07-07
forum: General Help
---

### Post by Psyphre on 2009-07-07
Hi,

The past month my applications have been having random crashes. Its totally random and happens on multiple programs (Though I have a feeling it affects all of them).

Some examples:

- Eye of gnome (the image viewer) randomly crashes after openeing a few images. It can work perfectly, then sudenly I open a picture and it crashes.

-Evolution sometimes crashes when opening mail, or creating a new mail.

-Gimp can randomly crash when opening files

-Nautilus randomly crashes when opening up a browser window. This usually means my desktop dissapears after the crash and I have to relog back in.


Now ive managed the recreate it using terminal and opening multiple nautilus instances until it crashes. Unfortunately for some reason nautilus doesnt show any information in terminal so I cant see whats causing the issue. I tried doing the same with eye of gnome, but couldnt repeat the crash (even though eye of gnome crashes the most often out of all my applications).

Is there someplace where these logs are kept? So that when I next have an application crash, i can view the logs and see whats causing it.

Ive been using ubuntu for years and its the first time ive had this kind of problem, no idea what could be causing it.

Thanks

---

### Post by wojox on 2009-07-07
All logs are stored in /var/log directory under Ubuntu.

See if there's an apport.log - application crash report / log file

---

### Post by c0mput3r_n3rD on 2009-07-07
you can run the application and redirect the error to a file, like so:

```

./myProgram 2>> myPrograms_errors.txt
```

---

### Post by japadamaray on 2009-07-07
It sounds to me like there may be some problems with your hard disk, which you can check for with fsck.

---

### Post by Psyphre on 2009-07-07
Sorry I did not make it clear, but its pretty random. I could go hours and open up 100 pictures with no crash, or it could crash 5 times in an hour. 

Thank you all for your responses.

**wojox: **Conviniently the image viewer crashed, I opened up images one after the other until it crashed. Then looked in var/log/ but no apport.log file.
[B]
c0mput3r_n3rD:[/B] Do i have to do that everytime i want to open a program? Because like i said its could take hundreds of times of opening an app before i can crash it. If i only have to do that command once, then thats brilliant.

by the way i assume if its the image viewer i do something like this?
./eog 2>> eog_errors.txt

**japadamaray:** I know fsck runs at bootup from time to time, but how do i set it to run manually?

---

### Post by Psyphre on 2009-07-07
update, i did it the long fashioned way. Just opened up pictures one at a time with terminal, i was lucky that it didnt taket too long, after opening 10 terminal windows and opening images on each, by the time i reached my 7th image it crashed.

Nothing showed up in any of the terminals except the one i used to open the first image. It simply said: **Segmentation fault**

Although I havent tried it with other applications, i assume its probably the same reason.

What exactly is a segmentation fault?

---

### Post by wojox on 2009-07-07
A segmentation fault (often shortened to segfault) is a particular error condition that can occur during the operation of computer software. A segmentation fault occurs when a program attempts to access a memory location that it is not allowed to access, or attempts to access a memory location in a way that is not allowed (for example, attempting to write to a read-only location, or to overwrite part of the operating system).


[http://en.wikipedia.org/wiki/Segmentation_fault](http://en.wikipedia.org/wiki/Segmentation_fault)

---

### Post by wojox on 2009-07-07
Check this out as well

Apport is not enabled by default in stable releases, even if it is installed. There are two ways to enable it.

    * If you want to debug a specific program once, just do:

      sudo force_start=1 /etc/init.d/apport restart

[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

---

### Post by Psyphre on 2009-07-07
> **wojox said:**
> A segmentation fault (often shortened to segfault) is a particular error condition that can occur during the operation of computer software. A segmentation fault occurs when a program attempts to access a memory location that it is not allowed to access, or attempts to access a memory location in a way that is not allowed (for example, attempting to write to a read-only location, or to overwrite part of the operating system).


[http://en.wikipedia.org/wiki/Segmentation_fault](http://en.wikipedia.org/wiki/Segmentation_fault)

Thx wojox, i did a quick google b4 asking, but i dont know what causes it. I mean, is it my hardware failing or ubuntu? Is it harddrive, RAM etc.

---

### Post by synapsys on 2009-07-07
Sounds like a RAM issue to me. It would be a good idea to run memtest.

If you don't have memtest as a boot option in grub then download and burn a memtest cd and boot to it. (preferably from another computer)

Totally random crashes....
Seg fault...
probably ram.....

---

### Post by wojox on 2009-07-07
It's usually software related.

Try that command in terminal

```
sudo force_start=1 /etc/init.d/apport restart
```

See what it says.

---

### Post by Psyphre on 2009-07-08
synapsys: Thx, will do a memtest.

Wojox: Yup did that and my image viewer crashed after opening a few pictures. It uploaded a report and also created an apport log. I took a look at the apport log and it said:

```
apport (pid 16837) Wed Jul  8 03:04:51 2009: called for pid 16827, signal 11
apport (pid 16837) Wed Jul  8 03:04:51 2009: executable: /usr/bin/eog (command line "eog /home/ed/img.ashx")
apport (pid 16837) Wed Jul  8 03:05:04 2009: wrote report /var/crash/_usr_bin_eog.1000.crash
```

The .crash file in /var/crash/ doesnt seem to say what caused the crash. It only lists my computer specs, the program dependencies and a LOT of garbled letters (must be code). Heres an example:
```
+NuL3rpp+dtBF3zWW0yWZf0TnfE+t/3S6X9T0c4DO9Yuafs47aR9nLKdTM
```



update: Did a memtest and after leaving it for an hour I came back to "pass complete, no errors. Press ESC to exit". Looks likes memtest is clean, however what i find interesting is that my ram used to say 2.0gb a while back in ubuntu system monitor. But now it says 1.9gb. Dont know if thats relevant or not.

---

