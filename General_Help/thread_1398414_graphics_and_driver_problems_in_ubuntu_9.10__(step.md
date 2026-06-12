---
title: "graphics and driver problems in ubuntu 9.10  (step by step process included)"
date: 2010-02-04
forum: General Help
---

### Post by zerobotman on 2010-02-04
so i've had some trouble recently installing my drivers in ubuntu 9.10. i'll include a point form list of problems and my attempts at solving them in case you don't want to read this whole story (see list of events below this paragraph). to give a bit of background as to my problem (in case it may be relevant) i had installed kubuntu (later converted to ubuntu do to user friendliness) after procuring a new hard drive after the last one was believed to be defective. asside from crashing and becoming unreadable/uninstallable my previous operating system on my last hard drive (windows 7 retail) had a peculiar problem where it would only display games in a tiny window taking in the center of the screen that was only perhaps %25 of the entire screen. what puzzles me is how this tiny screen problem has transfered not only from computer os to os but persisted even after a hard drive replacement and completely fresh install. naturally my first plan was to reset my bios to default settings thinking this was a way that the video settings could have remained. this did not work. i then proceeded to install drivers via "system, administrator, hardware drivers" although the driver installer hung at %25 and didn't continue for 6 hours straight. i then installed ENVY which also hung at %50. i later attempted to install the drivers manually by downloading NVIDIA-Linux-x86_64-195.30-pkg2.run however even after doing the "ctrl, alt, f2" combination, signing in as root, typing "init 3", typing "killall gdm", and then extracting/running the driver it still stated that x server was running and would not install. now that you know why and how i did what i did and how, does anyone know how to fix that resolution problem or install my drivers? anyway in case this wasn't clear or you didn't want to read this whole thing i'll put it in a point form list below 

[FONT=Arial Black]LIST Of EVENTS
[FONT=Arial]
[/FONT][/FONT]
[LIST]
[*]Windows 7 develops resolution problem. games appear in tiny boxes in center of screen surrounded by black.
[*]Windows 7 dies
[*]Hard drive replaced
[*]kubuntu installed
[*]kubuntu exhibits same small box problem
[*]kubuntu converted to ubuntu for user friendliness
[*]ubuntu continues to exhibit small box problem
[*]used "system, administrator, hardware drivers" though nvidia drivers hang at %25
[*]installed ENVY though it too hangs but at $50
[*]downloaded NVIDIA-Linux-x86_64-195.30-pkg2.run
[*]typed "ctrl, alt, f2"
[*]signed in at prompt
[*]typed "sudo init 3"
[*]typed "cd /home/*username*/Downloads"
[*]Typed "sudo chmod +x NVIDIA-Linux-x86_64-195.30-pkg2.run
[*]typed "sudo ./NVIDIA-Linux-x86_64-195.30-pkg2.run"
[*]nvidia installer claimed it could not run while x server was running
[*]posted on ubuntu forums about my troubles
[/LIST]
[FONT=Arial Black]System Specs
[/FONT]
Name: Lenova T61
CPU: T8100 2.10 ghtz
MEM: 3gb ddr2
HD: 80gb
CD/DVD: cdrw dvdr
OS: Kubuntu 64bit converted ubuntu 64bit

i appreciate any help you guys can give and would be happy to provide any info you would need.
[FONT=Arial Black][FONT=Arial][/FONT][/FONT]

---

### Post by mavmic on 2010-02-04
nice article

---

### Post by mavmic on 2010-02-04
i had the same problem

---

### Post by zerobotman on 2010-02-04
hmm google is having a bit of trouble translating the link. what problem specificly are you having in common?

---

### Post by patchwork on 2010-02-04
Not sure about the original problem, but to install the new nvidia driver this should work:

Before attempting to install the NVIDIA-Linux-x86_64-195.30-pkg2.run package, you must stop the X server.  From terminal, type ```
sudo service gdm stop
```This will drop you out of X and into the cli.  Next, ```
cd /path/to/NVIDIA-Linux-x86_64-195.30-pkg2.run
```Start the command:
```
./NVIDIA-Linux-x86_64-195.30-pkg2.run
```This should run the installer.  When finished, reboot using ```
sudo shutdown -r now
```Hope this helps.

---

