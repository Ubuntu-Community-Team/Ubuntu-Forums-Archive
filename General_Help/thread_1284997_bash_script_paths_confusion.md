---
title: "bash script paths confusion"
date: 2009-10-07
forum: General Help
---

### Post by garuff on 2009-10-07
Hi,
Bear with me, I'm new to scripting and the like (and still relatively new to ubuntu etc)...

So I've written a simple script that will take a downloaded real audio stream and convert it to .mp3

```
#!/bin/bash
# Gareth's Iplayer download script

echo "Please enter the day of the week (no capitals)"
read RECDAY
echo "Please enter the show date; eg 20090531"
read SHOWDATE

mplayer /home/g/Desktop/radio_2_-_"$RECDAY"_2000.ra -vc null -vo null -ao pcm:fast:waveheader:file=RCM"$SHOWDATE"_raw.wav

lame -V 6 RCM"$SHOWDATE"_raw.wav /home/g/Desktop/RCM"$SHOWDATE".mp3

id3v2 -a "Radcliffe & Maconie" -A "Radio 2 Shows" -t ""$RECDAY" "$SHOWDATE"" /home/g/Desktop/RCM"$SHOWDATE".mp3

rm RCM"$SHOWDATE"_raw.wav
```fine... that works, no troubles there.
My issue is that even though I've put this in ~/bin/ and amended my .bashrc (I don't have either .bash_login or .bashprofile files existing) to map the path to ~/bin, I still can't run this command using just the script name (i.e. without the .sh filetype or specifying where the script is located).

AFAIK this is something to do with me needing to set the paths that bash will look for scripts in, but I can't seem to get my head round it as all of the posts/instructions I've found so far are amending files that I don't seem to have?!

This isn't even important for this script, but it's bugging me as I got it to work yesterday, but when I logged back in today it didn't work and I've since failed to get it to work!
Anyone actually get what I'm talking about!?
Thanks in advance,

Gareth

---

### Post by andrew.46 on 2009-10-07
Hi Garuff,

Could you post the exact line you used in ~/.bashrc to add ~/bin to the $PATH? And another thought: have you made your script executable?

All the best,

Andrew

---

### Post by geirha on 2009-10-07
If your script is ~/bin/myscript.sh, executable, and ~/bin is in PATH, then you must type myscript.sh to execute it. Linux does not determine filetype by extension (as windows does), but rather by content. The first line in your file, "#!/bin/bash" (the hash-bang) tells linux that this is a bash script. 

I know it's common to put .sh extension on bash-scripts, but it's actually bad practice. If you really do want an extension, it should be .bash for bash scripts, .sh for posix shell scripts. But as I mentioned, the extension doesn't matter. Just name it ~/bin/myscript  ... without extension.

---

### Post by garuff on 2009-10-08
andrew:
export PATH=$PATH:/home/g/bin

is the line I added to bash.rc

but I think geirha might have hit the nail on the head there... my first line is indeed #!/bin/bash ... but the various bits I'd read to learn about scripting had all said to call it filename.sh ... makes sense that therefore that was what I had to type to get it to run!
So if I ditch the .sh, the only real implication will be that I won't know what kind of script it is without opening to check the first line?

---

### Post by mcduck on 2009-10-08
Actually Jaunty adds ~/bin to your path automatically if you just create that directory. But you need to log out and back again after you create the directory.

The problem with what you tried to do is using bash configuration files. Ubutnu handles most o the stuff with Dash, and only interactive user shells run bash as default..

Anyway, just check ~/.profile and you'll notice that adding ~/bin your path is already done for you. :)

What comes to the filename, you don't have to ditch the .sh extension if you don't want  to, but just don't execute your commands using "sh" instead just use "./" or "bash". If you use sh to tun the command you are specifically telling the system to run the script using the default shell (Dash) instead of bash.

So instead of running this:
```
sh yourscrpt.sh
```

use one of of these:
```
./yourscript.sh
/path/to/yourscript.sh
bash yourscript.sh
```
Ubuntu doesn't detect the program to use based on filename extension, so the extension is meaningless. The only problem was that you *told* the system to use sh instead of what was defined in the script.

---

### Post by geirha on 2009-10-08
> **garuff said:**
> 
So if I ditch the .sh, the only real implication will be that I won't know what kind of script it is without opening to check the first line?

Indeed. With the .sh extension you still won't know what kind of script is it either though, since it's become far too common to use .sh for both sh-scripts and non-sh-scripts. The file-command is handy when you'd like to see what type of executable, or filetype in general, you are dealing with.
```
file ~/bin/myscript
```

You'll also find that Ubuntu contains alot of scripts btw, and in general, they have no extensions. E.g. ```
file /bin/* | grep script
```

---

### Post by djurny on 2009-10-08
did you 'chmod +x ' your script? if the execute bit is not set, shell will not match your script, even if it is present in your path..

---

