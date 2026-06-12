---
title: "Hangs on startup then &quot;low graphics mode&quot;"
date: 2010-06-25
forum: General Help
---

### Post by Brandan2670 on 2010-06-25
I'm new to ubuntu, install was flawless, set up my email, chats everything was fine. Shut the computer off Weds night, turned it on Thurs now it won't boot. IS there a recovery anything built in so I can either repair the OS or get my file off the HD? Set up a dual boot of ubuntu so i could get my files but I dont know how to access them.

After a while I get the error "Ubuntu is running in low-graphics mode"
"your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself."

I press, OK I'm given several options. I can select them but they don't do anything. in respect to reconfiguring my hardware

I can however get to a terminal to type in code.

Any ideas?

---

### Post by supergrav on 2010-06-25
If you want to repair your installation you can either use a liveCD or when grub loads and you get to the selection screen choose the kernel with the notation "recovery" at the end! With these options you can certainly get to your files and copy them.

---

### Post by Brandan2670 on 2010-06-25
I did try booting from a live cd. Where are the files located I'm not used to the linux file system. They are in my 
Video and Pictures folders. 

Also, I did find some kind of recovery gui and tried the restore but it didn't work. no changes

---

### Post by wilee-nilee on 2010-06-25
> **Brandan2670 said:**
> I did try booting from a live cd. Where are the files located I'm not used to the linux file system. They are in my 
Video and Pictures folders. 

Also, I did find some kind of recovery gui and tried the restore but it didn't work. no changes

Try system-admin-hardware drivers in Ubuntu and see if your offered a driver for the graphics card. also run in the terminal and post.
```
lspci
```

---

### Post by supergrav on 2010-06-25
Since you enter command-line, your files are located in /home/"name-of-account"/Pictures and /home/"name-of-account"/Videos, where "name-of-account" is the username you use to login. You shoudl also be careful with capital letters, commands are case-sensitive. As for the recovery gui I'm afraid I'm not able to help you...It is a long time since I performed a system recovery and I don't remember much! In general, my advice is to work with command line tools, you get better control of the situation!

---

### Post by Brandan2670 on 2010-06-25
> **wilee-nilee said:**
> Try system-admin-hardware drivers in Ubuntu and see if your offered a driver for the graphics card. also run in the terminal and post.
```
lspci
```

What is the exact line of code i should try?

Also, I did find my files when booting off the live CD thank you. But, linux tells me i do not have permission to read them. is there a way to change the attributes of the file?

---

### Post by wilee-nilee on 2010-06-25
I think this is a fixable problem.
run in the terminal ```
lspci
```
Then copy and paste the results in the terminal to a reply. This command will identify your hardware including the graphics card. Did you look in the hardware drivers as I suggested to see if any are offered. This is done in the installed Ubuntu.

To get into the computer with low graphics mode to look in hardware drivers; at the grub menu hit e then using the arrow keys put nomodset at the end of the kernel then hold down the ctrl key and hit x

Also did you install Ubuntu from a live windows environment or did you boot the live cd and install?

Also if you dual booted from a booted cd install there is a automatic 10 second countdown for you to choose the OS how long is the hang?

---

### Post by Brandan2670 on 2010-06-25
> **wilee-nilee said:**
> I think this is a fixable problem.
run in the terminal ```
lspci
```
Then copy and paste the results in the terminal to a reply. This command will identify your hardware including the graphics card. Did you look in the hardware drivers as I suggested to see if any are offered. This is done in the installed Ubuntu.

To get into the computer with low graphics mode to look in hardware drivers; at the grub menu hit e then using the arrow keys put nomodset at the end of the kernel then hold down the ctrl key and hit x

Also did you install Ubuntu from a live windows environment or did you boot the live cd and install?

Sorry no way to copy and paste is the best I could do...

My install took place off a cd i booted directly into the install

---

### Post by Brandan2670 on 2010-06-25
> **supergrav said:**
> Since you enter command-line, your files are located in /home/"name-of-account"/Pictures and /home/"name-of-account"/Videos, where "name-of-account" is the username you use to login. You shoudl also be careful with capital letters, commands are case-sensitive. As for the recovery gui I'm afraid I'm not able to help you...It is a long time since I performed a system recovery and I don't remember much! In general, my advice is to work with command line tools, you get better control of the situation!

Thats exactly where they were, do you know how i can change the permissions from terminal?

---

### Post by supergrav on 2010-06-25
> **Brandan2670 said:**
> Thats exactly where they were, do you know how i can change the permissions from terminal?

To change permissions you can either use chmod command or chown command. With chown you change ownership of the file or directory to another user and group. Probably what will be more useful to you is chmod with which you change permissions of the file and make it readable/writable/executable (the latter if it's possible to be executed). Basically run as root:
 chmod o+r and you will grant permission to everybody to read the file. I think it'll work for you!

---

