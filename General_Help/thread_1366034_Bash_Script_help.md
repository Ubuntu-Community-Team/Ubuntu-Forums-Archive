---
title: "Bash Script help"
date: 2009-12-27
forum: General Help
---

### Post by tom.swartz07 on 2009-12-27
Hi all,

I was sniffing around at OMG!Ubuntu earlier today, and I came across a bash script that changes your background to the daily Bing image. 

For some reason, it keeps throwing errors on my system.

Heres the full script```
#!/bin/bash
# bing wallpaper downloader by YoungJesus, 2009. 
# based on Siddharth Prakash Singh (http://www.spsneo.com/blog) php bing wallpaper downloader

# modify this, if you want to save to other place
#  - $HOME: your home dir
#  - %F: full date (%Y-%m-%d)
#  - other date format: man date :P
OUTPUT=`date "+$HOME/Pictures/bing_bg.%F.jpg"`

# get the bing.com page, and separate the background image (DONT touch this)
IMG=`wget -q http://www.bing.com -O- | sed -r "s/[\]//g;s/.*g_img=\{url:'([^']+)'.*/\1/gp;d"`

# get the background image to the output (DONT touch this)
wget -q "http://www.bing.com$IMG" -O "$OUTPUT"
# error handle
if [ $? -gt 0 ]; then
	echo "there is a problem with downloading.."
	exit 1
fi

# setup the background
gconftool-2 -s -t string /desktop/gnome/background/picture_filename "$OUTPUT"
# set the background position
#gconftool-2 -s -t string /desktop/gnome/background/picture_options "centered"
# set the background color
#gconftool-2 --type string --set /desktop/gnome/background/primary_color "black"

exit 0
```

its a shell script, so remember it has a .sh extension on it when you save it to run it.

Every time I try it, I get the error
```
tom@ubuntu-karmic:~/Dropbox/scripts$ ./bing_wallpaper.sh 
bash: ./bing_wallpaper.sh: /bin/bash^M: bad interpreter: No such file or directory

```


Can anyone shed some light on this?

---

### Post by falconindy on 2009-12-28
Chances are you've got that drive mounted with the 'users' flag, which implies noexec. You've got two options:

1) Explicitly specify 'exec' in /etc/fstab
2) Execute the script with 'bash ./scriptname'

---

### Post by tom.swartz07 on 2009-12-28
> **falconindy said:**
> Chances are you've got that drive mounted with the 'users' flag, which implies noexec. You've got two options:

1) Explicitly specify 'exec' in /etc/fstab
2) Execute the script with 'bash ./scriptname'

Not exactly sure what you meant by option number 1, so I tried option 2. Still doesnt work:```
tom@ubuntu-karmic:~/Dropbox/scripts$ bash ./bing_wallpaper.sh
: command not found: line 4: 
: command not found: line 10: 
: command not found: line 13: 
./bing_wallpaper.sh: line 30: syntax error: unexpected end of file

```

Would it work if I moved it explicitly to my Home folder?
EDIT: tried home folder, still doesnt work there and throws same error

Ive never seen a problem like this one before, out of the good dozen scripts I use, this is the only err-some one.

---

### Post by falconindy on 2009-12-28
The error you're getting now shows that the script is executing, but running into syntax errors. Oddly, seems to be directly related to blank lines.

---

### Post by tom.swartz07 on 2009-12-28
> **falconindy said:**
> The error you're getting now shows that the script is executing, but running into syntax errors. Oddly, seems to be directly related to blank lines.

Yeah that's what I noticed. Whitespace doesnt count in shell scripts though, does it?:confused::confused:

---

### Post by falconindy on 2009-12-28
> **tom.swartz07 said:**
> Yeah that's what I noticed. Whitespace doesnt count in shell scripts though, does it?:confused::confused:

Well, it shouldn't. Do try adding the 'exec' flag. You can remount partitions on the fly (yes, even root) as such:
```
sudo mount -o remount,defaults,relatime /dev/sdxy
```

---

### Post by tacantara on 2009-12-28
Normally, white space doesn't count in Bash scripts.  I've written a couple of simple scripts with space between lines, and it hasn't caused a problem.  Just for troubleshooting purposes, remove the lines or set them up as comment lines and see if that does the trick.

UPDATE:  I copied the script into a text file, set it as executable, and tested it.  I did get a new wallpaper, so the script appears to  work.  I even placed the script file on my desktop, and ran it from there.

---

### Post by tom.swartz07 on 2009-12-28
> **falconindy said:**
> Well, it shouldn't. Do try adding the 'exec' flag. You can remount partitions on the fly (yes, even root) as such:
```
sudo mount -o remount,defaults,relatime /dev/sdxy
```

Sorry, Im confused- add exec flag to what? The script? I already did chmod +x bing_wallpaper.sh

Or did you mean to my whole entire folder? That would be a bit overkill, I think...

EDIT: tacantara, already done, still doesnt fix it. Strangely enough- it still calls out the same lines as errors even after its changed and saved.



PS- congrats on 1,000 posts. that last one put you over the edge!

---

### Post by falconindy on 2009-12-28
Sorry, add exec to your mount options for the drive (defaults implies exec without users). Post the output of 'mount' so I can see what I'm up against.

> **tom.swartz07 said:**
> PS- congrats on 1,000 posts. that last one put you over the edge!
Bleh, I think I post here more often since I left Ubuntu...

---

### Post by tom.swartz07 on 2009-12-28
> **falconindy said:**
> Sorry, add exec to your mount options for the drive (defaults implies exec without users). Post the output of 'mount' so I can see what I'm up against.


Bleh, I think I post here more often since I left Ubuntu...

```
tom@ubuntu-karmic:~$ mount
/dev/sda8 on / type ext4 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda9 on /media/Data type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tom/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tom)

```

Need some help with adding the exec to my drive though...
sda8 is my root partition.

---

### Post by falconindy on 2009-12-28
Sure, sure.
```
sudo mount -o remount,defaults,errors=remount-ro /dev/sda8
```
As per the man page, defaults implies: rw, suid, dev, exec, auto, nouser, and async

This should work assuming that this action is taking place all on /dev/sda8. That is, your home directory isn't on a separate partition. Can I also assume /dev/sda9 is NTFS?

If this works and you'd like to make it permanent, we'll need to poke around in your /etc/fstab.

---

### Post by tom.swartz07 on 2009-12-28
> **falconindy said:**
> Sure, sure.
```
sudo mount -o remount,defaults,errors=remount-ro /dev/sda8
```
...
This should work assuming that this action is taking place all on /dev/sda8. That is, your home directory isn't on a separate partition. Can I also assume /dev/sda9 is NTFS?

If this works and you'd like to make it permanent, we'll need to poke around in your /etc/fstab.

nope, didnt work. Ran the command, tried to re-run the script, threw same errors as usual.

everythings on sda8, sda9 is an NTFS partition that i keep all of my music and movies.

---

### Post by falconindy on 2009-12-28
That's... highly peculiar. Perhaps your solution isn't down this road. I'm at a loss of both ideas and sleep. Sorry.

---

### Post by iponeverything on 2009-12-28
Your issue is with the file format. 

Install the "tofrodos" package and convert the script with the command:

dos2unix

---

### Post by stew721 on 2009-12-28
> **tom.swartz07 said:**
> Every time I try it, I get the error
```
tom@ubuntu-karmic:~/Dropbox/scripts$ ./bing_wallpaper.sh 
bash: ./bing_wallpaper.sh: /bin/bash***^M***: bad interpreter: No such file or directory

```Can anyone shed some light on this?
The first thing I noticed was the bash error; note the part I specifically bolded.  The system is trying to find "/bin/bash^M", but it should be "/bin/bash" though.  That error's due to the encoding of the file.  Use nano, vim, etc. to edit/recreate the file.  You can use dos2unix to convert the file as well; as stated in the post above mine. sed can be used to do an in-line replace as well: ***sed -i s/{ctrl+v}{ctrl+m}// filename*** if I remember correctly.

---

### Post by rnerwein on 2009-12-28
hello - i think - what you see is not what you get. what i think is, that your script is coming from DOS.
the output of your command "
bash: ./bing_wallpaper.sh: /bin/bash^M: bad interpreter: No such file or directory
" is the same if i do the command "unix2dos < script1 > script2" and try to run this.
the sign ^M is the end of line in MSdose. to convert the script you can use dos2unix.
--> available:  apt-get install tofrodos -- hope it will help you - ciao richi
sorry i ain't read all the comments up there - the other already told you what to do

---

### Post by rnerwein on 2009-12-28
hello - i think - what you see is not what you get. what i think is, that your script is coming from DOS.
the output of your command "
bash: ./bing_wallpaper.sh: /bin/bash^M: bad interpreter: No such file or directory
" is the same if i do the command "unix2dos < script1 > script2" and try to run this.
the sign ^M is the end of line in MSdose. to convert the script you can use dos2unix.
--> available:  apt-get install tofrodos -- hope it will help you - ciao richi

---

### Post by DaithiF on 2009-12-28
and just to add some more explanation, line endings in unix / linux consist of the 'newline' character, often denoted as '\n'
But in dos/windows, line endings consist of 2 characters together, newline '\n' and carriage return '\r'
to convert between the two formats is simply a case of adding or removing the carriage return character.
the dos2unix / unix2dos commands do this.  Or you can do it yourself using the sed command:
sed -i 's/\r$//' somefile       ==> replaces carriage return (\r) characters occurring at the end of a line, and so converts a dos/windows file to unix/linux
sed -i 's/$/\r/' somefile      ==> adds a carriage return character to the end of a line, and so converts in the opposite direction

---

### Post by tom.swartz07 on 2009-12-28
dos2unix did the job!

That was really strange that it was encoded that way, especially that it came from an Ubuntu blog...

Anyway- it works great now! 

Thanks everyone!

---

