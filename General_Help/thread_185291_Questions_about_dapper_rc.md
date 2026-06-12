---
title: "Questions about dapper rc"
date: 2006-05-31
forum: General Help
---

### Post by boyx on 2006-05-31
hey,
i have a few questions...

1. whenever i ghost my windows partition it overwrites the MBR and so dapper doesnt boot (i cant see the grub menu). how do i get it back? i read the wiki and it says that type "boot: rescue" at the splash screen...exactly where are how do i do that? i tried to go to additional options and deleted the entire default boot line and typed that in. however the kernel doesnt boot.

2. is there any symantic touchpad manager for GNOME like Ksynaptics for Kubuntu (KDE)?

3. i installed Gdesklets, and i want to install a new applet. when i install it using File > install new package, it installs correctly (i get a message that the package has been installed). however when i try to run that applet, i get an error saying that "sensor not found. This usually means that it has not been installed." 

can anyone help me?](*,)

---

### Post by ahaslam on 2006-05-31
[QUOTE=boyx]
3. i installed Gdesklets, and i want to install a new applet. when i install it using File > install new package, it installs correctly (i get a message that the package has been installed). however when i try to run that applet, i get an error saying that "sensor not found. This usually means that it has not been installed." 
[/QUOTE]


Hi, this wont help, but I have also had problems with Gdesklets. I installed a package, it said that it was successful but it wasn't to be found, yet alone ran. Whenever I've used Gdesklets I've had a poor experience. I thought It was just me, obviously not.

---

### Post by cleentrax on 2006-05-31
I have had no luck with gdesklets. Error messages, freezes, serious bugs, etc.

---

### Post by Sammi on 2006-05-31
To calm you guys down, can add that Gdekslets isn't very funvtional. There are other better ways of doing mostly all that it does. For instance many of it's functions have counterparts in the gnome panel, which are far more stable and easy to use. Examples: weather and system monitor.

---

### Post by steve.horsley on 2006-05-31
[QUOTE=boyx]hey,
i have a few questions...

1. whenever i ghost my windows partition it overwrites the MBR and so dapper doesnt boot (i cant see the grub menu). how do i get it back? i read the wiki and it says that type "boot: rescue" at the splash screen...exactly where are how do i do that? i tried to go to additional options and deleted the entire default boot line and typed that in. however the kernel doesnt boot.
[/QUOTE]
Almost right. You have to boot from the text-mode Ubuntu installer CD. At the **boot:** prompt, type **rescue** and press enter.

---

### Post by boyx on 2006-05-31
[QUOTE=steve.horsley]Almost right. You have to boot from the text-mode Ubuntu installer CD. At the **boot:** prompt, type **rescue** and press enter.[/QUOTE]
oh!! i was trying to do it from the regular live cd...is there any way to do it from the regular live cd since i dont have the text mode cd or do i have to download it just for this purpose...i hope not

---

### Post by blakamin on 2006-05-31
Start the install... 
go all the way thru to partitions, go "manually edit" and then tell it not to do anything to the partitions, 
it will exit to a menu... 
last thing there (from memory) is "install grub"

worked for me a week or 2 ago when I installed another distro that i deleted 10 minutes later) and it wrecked my grub

---

