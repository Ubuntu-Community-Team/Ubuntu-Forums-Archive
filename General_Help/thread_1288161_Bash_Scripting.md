---
title: "Bash Scripting"
date: 2009-10-11
forum: General Help
---

### Post by supersabre_22 on 2009-10-11
Hi guys,  I am very new here,  I am trying to create a simple script,  something along the lines :  

#!/bin/bash 
cd /home/example/;
./configure; 
make; 
make install;
cd /home/sabre/example2/;
./configure; 
make; 
make install;  

I kinda worked out I needed the ; at the end of commands (which took me ages to work out)  not sure when to use the ; and there's alot of documentation about && and other things, I have no idea .  I am getting ALOT of error when trying this.

---

### Post by barthel on 2009-10-11
It would be helpful if you could use the CODE tag to surround your script. Right now, I'm not entirely sure what your question is.

The semi-colon ";" is only needed when you want to put multiple commands on the same line. You could just as easily put the commands on separate lines.

However, I think you're also wanting to use "&&", which executes the next command **if and only if** the prior command succeeded. (No sense running "make" if configure failed, right?)

So let's tweak what you have above to this:
```
#!/bin/bash

cd /home/example
./configure && make && make install

cd /home/sabre/example2
./configure && make && make install

```

There are actually 2 major problems with this script.

[LIST=1]
[*]`make install` will fail unless run with root priviliges (e.g. sudo)
[*]Most of the errors you will encounter will not be bash errors
[/LIST]

There is also the minor problem that the script assumes your directories exist and contain the `configure` command.

Additionally, you may need to pass arguments to `configure`--something your simple script doesn't do.

Personally, I think you'd be much better off doing these steps individually. I have years of shell programming experience and my script to compile packages was *huge* because I wanted to trap and handle many different errors.

HTH

---

### Post by supersabre_22 on 2009-10-11
Thanks mate,

My main problem that I was experiecing was that it wouldn't change directory,

What I mean is,

cd /home/something
sudo ./configure

I want it to pretend that I am sitting infront of the machine and typing all this in,  it does NOT change directory,  a simpler example would be :

#!bin/bash
cd /home
ls

and if my 'pwd' was /etc

all i would see is a ls of /etc

This is probably my biggest problem

---

### Post by barthel on 2009-10-11
Wow, that's peculiar. I've never encountered that before.

Try this:
```

#!/bin/bash
ORIGINAL_WD=$(pwd)
echo $ORIGINAL_WD
echo "cd /etc"
cd /etc
pwd
echo "cd /home"
cd /home
pwd
echo "cd $HOME"
cd ~
pwd
echo "cd back to start"
cd $ORIGINAL_WD

```

`pwd` prints the current working directory. It should tell us if the cd was successful or not.

Oh--stupid question. Do those directories already exist?? I think I've encountered that kind of problem when I made a typo in a `cd` command...

(Guess that means I lied when I said I've *never* encountered it... :D )

---

### Post by supersabre_22 on 2009-10-11
#!/bin/bash
ORIGINAL_WD=$(pwd)
echo $ORIGINAL_WD
echo "cd /etc"
cd /etc
pwd
echo "cd /home"
cd /home
pwd
echo "cd $HOME"
cd ~
pwd
echo "cd back to start"
cd $ORIGINAL_WD


my current pwd is /etc, this is what I get when I run the script , the file is called dir_move.sh, 
it was created in notepad.exe (win32) and dumped in via Samba share here is the output: 
/etc
cd /etc
: No such file or directory line 5: cd: /etc
: command not foundmove.sh: line 6: pwd
cd /home
: No such file or directory line 8: cd: /home
: command not foundmove.sh: line 9: pwd
cd /home/sabre
: No such file or directory line 11: cd: ~
: command not foundmove.sh: line 9: pwd
cd back to start
: No such file or directory line 14: cd: /etc

You would think something like this would be SUPER easy,  or i must be really fuddling it up somewhere...

---

### Post by barthel on 2009-10-11
> **supersabre_22 said:**
> it was created in notepad.exe (win32) and dumped in via Samba share

That's very peculiar.

A few things I can think of:

[LIST=1]
[*]The problem might be MS-Windows end-of-line conventions. Try creating the file directly with an Ubuntu text editor. (This might also be why you thought you needed all those extra semi-colons....)
[*]The problem might be with your PATH. What does `echo $PATH` give you? (Except that `cd` is a shell builtin--so $PATH should be irrelevant.)
[*]Perhaps you're not actually using bash? What does `/bin/ls -l /bin/bash` give you? (Notice that I'm using the fully qualified path for the commands just to be on the safe side.)
[/LIST]

---

### Post by supersabre_22 on 2009-10-11
......
wow
....

Went into VIM, typed it manually, BOOM, works like a charm....

Yeah, WinBlows....

I can't even create scripts in Kodomo IDE 5.... it fails there too!!!

Downloading VIM for windows..

I'm trying experiments with Ubuntu Server without any GUI, so,  Copy and Paste is out the windows,  

Thanks for your help mate.

---

### Post by barthel on 2009-10-11
If you're using VIM (good choice BTW), you can change the end-of-line conventions between dos, mac, and unix.

Look under Edit -> File Settings -> File Format.

Just an FYI: this goes back to the old days of computing, when dinosaurs like CP/M still ruled the earth. Some systems chose ASCII 13 (CR, Carriage Return) as the EOL character. Some chose ASCII 10 (LF, Line Feed). Some, like MS-DOS, required both.

As a result, there was no such thing as "plain text" when you were transferring between systems. You nearly always had to perform some sort of EOL conversion.

Glad we found the problem. Good luck!

---

### Post by JedMeister on 2009-10-29
Sounds like you're all sorted but just wanted to add my 2c as a long time Win user but now running a headless Ubuntu based server (administered from Win desktop - I would be running Ubuntu desktop if it weren't for my son's games).

I use PuTTY (provides a SSH remote terminal) to connect to the server - so copy+paste from the net or other sources is easy! (I often use my locally based wiki for documenting my steps)
I will sometimes edit scripts from the terminal (through PuTTY) but usually I access/copy them with FileZilla (FTP) and edit with Notepad++ which by default saves in a format compatible with Linux scripts. (It must adjust the EOL character by extension though as .txt .cmd .bat .vbs files edited by Notepad++ all work correctly in Win.)

You could achieve the same ends by making Vim for Win default text editor in FileZilla I'd imagine

---

