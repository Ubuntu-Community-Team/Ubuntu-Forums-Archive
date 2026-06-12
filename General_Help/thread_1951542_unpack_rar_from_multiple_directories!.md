---
title: "unpack rar from multiple directories!"
date: 2012-04-02
forum: General Help
---

### Post by Krillezz on 2012-04-02
Hi! 
I am having an issue where i have a folder, containing many subfolders, wich each contain a .rar file, is there any cool bash script i can do to loop over my folders and unpack all the files to my beginning folder?

i.e there is folder /tmp/ which has 4 subfolders  /tmp/A, /tmp/B, /tmp/C and  /tmp/D, in each of these folders there is an .rar which i want to extract to /tmp/

How can this be achieved? I don't really have time/patience to do this manually and i realize you people probably have other things to do and such, but i hope you may find the time.

---

### Post by papibe on 2012-04-02
Hi Krillezz. Welcome to the forums!

If the rar files are self contained (no parts), you can use the command 'find' to get all your rar files and then execute an 'unrar' command for each of them:
```
find /tmp -iname '*.rar' -exec unrar e '{}' /tmp \;
```
This requires you have installed the tool 'unrar'. If it's not installed, do it like this:
```
sudo apt-get install unrar
```
I hope that helps, and tell us how it goes.
Regard.

---

### Post by Krillezz on 2012-04-02
Wow thanks! that was quick! if the rars are in parts, what should i do then?
there is still only 1 .rar file, the rest is r00 ,r01 and so forth

/Edit it worked very nice! when i tried it, or at least this far, gonna let it work during the night and hopefully it will be done by tomorrow :)

a little follow up question! can i somehow put this in a script where i get the path to search and to put everything it finds in the same folder as from where the script is run? :)

ie i run /tmp/script.sh and it does what you showed me
and then i run /anothertmp/script.sh and every unpacked file ends up under /anothertmp/?

thanks again! saved me a TON of time :)

---

### Post by papibe on 2012-04-02
You are very welcome ;)

The command for decompress multiple parts doesn't change at all. However, unrar has to be executed on the the subdirectory where the parts reside (so it can find them).

The previous command run each 'unrar' command where it's being executed. To run each command on the subdirectory where a file is found, change the option -excec for -execdir:
```
find /tmp -iname '*.rar' **[COLOR="Red"]-execdir[/COLOR]** unrar e '{}' /tmp \;
```
Now that I think about it, this last command cover both cases (it does not change the results for no-part rars).

Hope that helps, and tell us how it goes.
Regards.

---

### Post by papibe on 2012-04-02
Hey! good to hear that.

I didn't see you other question earlier. In order to keep the conversation going, and specially for asking a new related question, is better to make a new replay ;)

> **Krillezz said:**
> can i somehow put this in a script where i get the path to search and to put everything it finds in the same folder as from where the script is run? :)

ie i run /tmp/script.sh and it does what you showed me
and then i run /anothertmp/script.sh and every unpacked file ends up under /anothertmp/?
Yes.

Here's what I recommend.

Put it on a bash script. Let's say it is called myuntar.sh:
```
#!/bin/bash
find ./ -iname '*.rar' -execdir unrar e '{}' ./ \;
```
(I later comment on the directory changes).

Then give the script execute permission:
```
chmod a+x myuntar.sh
```
Then I would recommend creating a 'bin' directory on your home, and moving the script there:
```
mkdir bin
mv myuntar.sh bin/
```
That way (for all new terminals) will be available to run anywhere as is if where installed on the system (~/bin/ is added to the system path if exists).

As you see, I changed the '/tmp' directory for './'. That's a reference to the current directory. Thus the script starts looking for rars from where it is called, and decompress in the same place.

I hope that points you in the right direction.
Regards.

---

### Post by Krillezz on 2012-04-03
You sir, are awesome :)
/although i cant run it from anywhere, the script is still awesome :)
/second edit, ofcourse it works, just had to to a reboot
thanks again! I did learn a lot from your help! and the ability to add my own commands to the system shell! Golden!

---

### Post by Krillezz on 2012-05-11
Just had to say thanks again, you have no idea how much this helped :guitar:

---

