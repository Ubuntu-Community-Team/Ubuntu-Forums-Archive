---
title: "Terminal Help"
date: 2010-03-14
forum: General Help
---

### Post by HunterAnderson on 2010-03-14
Hey. I needed some help with terminal(obviously by the title). Sometimes ill have to type in several commands with file locations and mess it it gets kinda old because, like for example theres a program i have. To run it i have to type some thing along the lines of this:

cd /media/........./GameEditor
chmod +x gameEditor
./gameEditor

i no this isnt that much but you get the point. i was wondering if there is a way to create a file with this, or even other commands to be preformed, in it and then beable to run those commands in order anytime you want through that file. It may not be possible but if so any ideas would be awesome. If it isnt possible then oh well thats cool to.

---

### Post by richardjh on 2010-03-14
What you are describing is a shell script (or bash script)

You have already done what you need to do. 
Type all the commands you need to run into a file, eg my_script.sh.

Then make that file executable using 

```
chmod +x my_script.sh
```Then to run all of those commands in that file just do :

```
./my_script.sh
```If you create a folder called bin in your home directory, you should be able to run the file without changing to that directory by just typing my_script.sh.

This is because ~/bin is in your path.

If anything doesn't work as described post back and I will help you get this working. It is really useful to be able to work with shell scripts.

Also the script doesn't have to end with a .sh extension it is just an example.

---

### Post by Penguin Guy on 2010-03-14
There are two main ways to do this, both require a bit of shell mumbo-jumbo.

[LIST=A]
[*]**Scripts:**
[LIST=1]
[*]Make a script directory: [FONT="Courier New"]mkdir ~/bin[/FONT] or [FONT="Courier New"]mkdir ~/.bin[/FONT] if you want it to be hidden.
[*]Add an entry to your profile that automatically adds the folder to your path every time you login:
```

echo 'if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
if [ -d "$HOME/.bin" ] ; then
    PATH="$HOME/.bin:$PATH"
fi' >> ~/.profile

```
[*]Logout and back in again and you will now be able to use your script directory.


[/LIST]
[*]**Aliases:**
[LIST=1]
[*]Make an alias file: [FONT="Courier New"]touch ~/aliases[/FONT] or [FONT="Courier New"]touch ~/.aliases[/FONT] if you want it to be hidden.
[*]Add an entry to your bashrc that automatically processes the file every time you login:
```

echo 'if [ -f "$HOME/aliases" ]; then
    . "$HOME/aliases"
fi
if [ -f "$HOME/.aliases" ]; then
    . "$HOME/.aliases"
fi' >> ~/.bashrc

```
[*]Logout and back in again and you will now be able to use your alias file
[/LIST]
[/LIST]

Attached below are two files; my alias file with some common commands that I use, and my [FONT="Courier New"]x[/FONT] file - which makes all the scripts in it's surrounding directory executable (I use this in my [FONT="Courier New"]bin[/FONT], so I just type [FONT="Courier New"]x[/FONT], and all my executables will be automatically made, well, executable).

---

### Post by blueridgedog on 2010-03-14
The chmod part should only need to be done once, from there on, you should be able to just run the application with 
/media/........./GameEditor/gameEditor

After you run it once, you can get to it again with the "up" arrow on the keyboard.

---

### Post by HunterAnderson on 2010-03-15
Thanks alot richardjh. Huge help. I was havin some trouble with the whole bin in the home directory thing. just to make sure im doing it right it is 
/home/hunter/bin
and not
/home/bin
the x.sh shell worked great to. im still not very familar with the whole alias and profile stuff so i probably need to go read up on that some before i can get that down. Thanks alot both of you. im slowly learning all of this stuff.

---

### Post by Penguin Guy on 2010-03-16
> **HunterAnderson said:**
> I was havin some trouble with the whole bin in the home directory thing. just to make sure im doing it right it is 
/home/hunter/bin
Yeah, that's right. Maybe you should try deleting the previous entry in your [FONT="Courier New"].profile[/FONT] and try running my command again? If that fails, post the contents of your [FONT="Courier New"].profile[/FONT] and [FONT="Courier New"].bashrc[/FONT] files here so we can see what went wrong.

---

