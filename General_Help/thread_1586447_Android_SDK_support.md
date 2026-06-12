---
title: "Android SDK support"
date: 2010-10-02
forum: General Help
---

### Post by barnacles on 2010-10-02
Hey everyone, 

First and foremost, if this is in the wrong section please move it. 

I hope someone here might be able to help. I've recently switched back to Ubuntu and using an android phone makes it important for me to have adb. So I began setting it up. I've followed androids guidelines for configuring it all and I've extracted my sdk folder into my home folder.

Now, when I try adb commands from /home/usr/android-sdk/tools I get an error that adb is not a command.

I can use "export PATH=$PATH:/home/user/android-sdk/tools" to get it running, but if I exit terminal and reenter I will get the same error unless I run the above command. Does anyone know how I could fix this?

Thanks

---

### Post by lykeion on 2010-10-02
Couldn't you just add the path in ~/.bashrc to make it stick```
gedit ~/.bashrc
```add this 
```
export PATH=$PATH:/home/user/android-sdk/tools
```

---

### Post by barnacles on 2010-10-03
My first two lines of my bashrc are as follows already:

#AndroidDev PATH
export PATH=$PATH:home/usr/android-sdk/tools

Still: adb: command not found

---

### Post by Sub101 on 2010-10-03
Mine is:

```
export PATH=${PATH}:$HOME/android-sdk-linux_86/tools

```

I dont know if the {} make a difference though?

Have you opened a new terminal after the changes?

---

### Post by barnacles on 2010-10-03
> **Sub101 said:**
> Mine is:

```
export PATH=${PATH}:$HOME/android-sdk-linux_86/tools

```

I dont know if the {} make a difference though?

Have you opened a new terminal after the changes?

Yes, and I have used both {PATH} and PATH, opening a new terminal after each gedit.

---

### Post by lykeion on 2010-10-04
> **barnacles said:**
> My first two lines of my bashrc are as follows already:

#AndroidDev PATH
export PATH=$PATH:home/usr/android-sdk/tools

Still: adb: command not found

A detail here, but I see you omitted the dot before bashrc. Be sure to edit the right file, i.e ~/.bashrc
1. Go to your home dir
```
cd
```
2. Open the .bashrc file (don't forget the dot)
```
gedit .bashrc
```
3. Add the export PATH line, close and save the file.
I see you've tried /home/user/android-sdk-linux_x86/tools.
the "user" part should be replaced by your username, or easier you could use the $HOME variable like this (supposing you've installed Android SDK in your home directory)
```
export PATH=$PATH:$HOME/android-sdk-linux_x86/tools
```
4. Instead of starting a new terminal you can simply do
```
source .bashrc
```
5. To make sure the android tools dir is in the path echo your path to output
```
echo $PATH
```
6. If it is you should be able to use the adb command directly

---

### Post by barnacles on 2010-10-05
> **lykeion said:**
> A detail here, but I see you omitted the dot before bashrc. Be sure to edit the right file, i.e ~/.bashrc
1. Go to your home dir
```
cd
```
2. Open the .bashrc file (don't forget the dot)
```
gedit .bashrc
```
3. Add the export PATH line, close and save the file.
I see you've tried /home/user/android-sdk-linux_x86/tools.
the "user" part should be replaced by your username, or easier you could use the $HOME variable like this (supposing you've installed Android SDK in your home directory)
```
export PATH=$PATH:$HOME/android-sdk-linux_x86/tools
```
4. Instead of starting a new terminal you can simply do
```
source .bashrc
```
5. To make sure the android tools dir is in the path echo your path to output
```
echo $PATH
```
6. If it is you should be able to use the adb command directly

Thank you sir. I left out the details of my specific paths just to make it as simple as possible. However, I think my problem must have been in my .bashrc. (knew about that period too :D) but I think I had the wrong path. None the less it seems to be working now.. ::crossing fingers that it sticks::

Side note, maybe you can help. Every time I open terminal I get a 

```
$:command not found
dave@dave-laptop:~$
```

Not a huge deal, but I'm curious why its doing this. Any idea?

Again, I appreciate the help.

---

### Post by lykeion on 2010-10-05
Good that it has worked out. You may want to tag this thread as SOLVED to help others find solutions easily.
About the "command not found": Maybe you have left something in .bashrc that shouldn't be there (like an extra semicolon in the PATH line?)

---

### Post by barnacles on 2010-10-05
Thank you I will mark it solved. 

And I did something cause I found "$ sudo gedit ~/.bashrc" creeping at the bottom of my .bashrc. haha

Thanks a lot for all your help. Much appreciated.

---

