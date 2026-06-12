---
title: "Bash Scripting Questions"
date: 2010-01-25
forum: General Help
---

### Post by conradin on 2010-01-25
Hi All, 
I am just starting with BASH programing and I'm not sure what to do first. Can anyone point me to a good tutorial or HOWTO? My primary question is how do I compile BASH scripts once I write them in a text editor like gedit?

I am coming from a background in C++. How much is BASH scripting like other programing languages?

---

### Post by yousillygoose on 2010-01-25
You don't need to compile a script to run it.  You can do a:

chmod +x scriptname 


to make it executable.  To run the script:

./scriptname

---

### Post by sgosnell on 2010-01-25
Scripts are more like DOS batch files.  They're just text files, but you need to make them executable.

---

### Post by conradin on 2010-01-25
Ok, That helped! But I have another question. when I run my script, a dialog box appears saying my script is an executable. Then it gives 4 options, "run in terminal" , "Display" , "Cancel" ,and "Run". How can I make this script run in the terminal (or elsewhere) without any interference?

What is the diference between "Run" and "Run in the Terminal"? (yes, I tried it, I never see my script run when I select run. Does Run launch a background process?

---

### Post by kjohri on 2010-01-25
Bash scripts are normally run from command line. So to execute a bash script, open a terminal, go to the directory where script file is located (or type the absolute file) and give the command

./script_filename

You can also schedule a bash script to run periodically using cron.

For an excellent coverage of shell programming refer to the book, "Unix Programming Environment" by Brian W. Kernighan and Rob Pike. [http://cm.bell-labs.com/cm/cs/upe/]("http://cm.bell-labs.com/cm/cs/upe/")

---

### Post by D3V11 on 2010-01-25
> **conradin said:**
> Ok, That helped! But I have another question. when I run my script, a dialog box appears saying my script is an executable. Then it gives 4 options, "run in terminal" , "Display" , "Cancel" ,and "Run". How can I make this script run in the terminal (or elsewhere) without any interference?

What is the diference between "Run" and "Run in the Terminal"? (yes, I tried it, I never see my script run when I select run. Does Run launch a background process?

You can run them from the terminal. If you don't you should make sure you have something in the script to kill the process when it's done because they can keep running like the energizer bunny if you don't...over, and over, and over... Sometimes I will make a custom launcher for them. After you give them executable permission make the command for the launcher (if you save them in your home folder. I do as it cuts down on having to input path names)
```

./scriptname

```
or if you want it to open in a terminal
```

gnome-terminal -e ./scriptname

```

---

### Post by sgosnell on 2010-01-26
./ means 'current directory'.  By default, Linux only looks for executables in the path, and not in the current directory.  You need to specifically tell it to look in the current directory by prefacing the filename with ./.

---

### Post by oldfred on 2010-01-26
You can put your scripts into the hidden file in your home directory:

~/.gnome2/nautilus-scripts

and then when browsing right click scripts, it will show you the scripts in that folder ready for executing.

---

### Post by jamesisin on 2010-01-26
If you Run In Terminal, it will run the script in a terminal window but the window will close immediately upon script completion.  A short script will vanish very quickly.  Run doesn't bother displaying a terminal.

You have been given some good options for placing and using scripts.  About half way down in this post I discuss script storage/placement:

[http://www.soundunreason.com/InkWell/?p=1335](http://www.soundunreason.com/InkWell/?p=1335)

This will give you some options and some understanding as well.

---

### Post by conradin on 2010-02-03
Thank you everyone for helping me get started! My questions are answered!

---

### Post by jamesisin on 2010-02-03
Excellent.  Please mark your thread as SOLVED in Thread Tools above.

---

