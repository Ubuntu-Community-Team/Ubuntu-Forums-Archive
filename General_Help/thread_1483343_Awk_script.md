---
title: "Awk script"
date: 2010-05-14
forum: General Help
---

### Post by sandyd on 2010-05-14
I currenty need some help with awk for a program im working on.

Im currently outputing the contents of a file, then passing it through awk.

However, if I pass it through awk, and output it to a file, it shows up blank.

script below:
```

cat /etc/default/grub | sudo awk -F "GRUB_CMDLINE_LINUX_DEFAULT" '{print $1}' > /etc/default/grub
```

---

### Post by dabl on 2010-05-14
If you're working as a user, you don't have permission to write to /etc/xxxxxxx.

Try outputting it to your /home folder.

---

### Post by sandyd on 2010-05-14
> **dabl said:**
> If you're working as a user, you don't have permission to write to /etc/xxxxxxx.

Try outputting it to your /home folder.

I did output to the home folder.
I just changed the script back to what it was origionally before I modified it to output to my home folder

---

### Post by rnerwein on 2010-05-14
hi
may be a silly question. but how does your /etc/default/grub looks like ???  :-)
ciao

---

### Post by gmargo on 2010-05-14
What are you trying to accomplish?

---

### Post by DaithiF on 2010-05-14
Hi,

redirecting a file back onto itself clobbers the file, the output redirection opens the file for writing (and thereby deletes the existing contents), before the first link in the chain of pipe commands gets to read anything.  so use an intermediate temporary file.  Or depending on what you want to do, sed may be a better bet, you can use the -i parameter to do an inplace update and avoid the need for the intermediate file.

---

### Post by sandyd on 2010-05-14
> **DaithiF said:**
> Hi,

redirecting a file back onto itself clobbers the file, the output redirection opens the file for writing (and thereby deletes the existing contents), before the first link in the chain of pipe commands gets to read anything.  so use an intermediate temporary file.  Or depending on what you want to do, sed may be a better bet, you can use the -i parameter to do an inplace update and avoid the need for the intermediate file.
ah, thats it! thanks!

---

### Post by sandyd on 2010-05-14
one last question.
```


SCREEN_SIZE= xdpyinfo | grep dimensions | awk -F "dimensions:    " '{print $2}' | awk -F " pixels" '{print $1}'
SCREEN_DEPTH= xdpyinfo | grep depths | awk -F ":    " '{print $2}' | awk -F ", " '{print $1}'
echo $SCREEN_SIZE
echo "This script will (hopefully!) fix your plymouth splash resolution"
echo "This is still beta, so please be careful"
echo "All files script edits will be backed up with a .bak extension"


cat /etc/default/grub | sudo awk -F "GRUB_CMDLINE_LINUX_DEFAULT" '{print $1}' > grub
cat /etc/default/grub | sudo awk -F "GRUB_GFXMODE" '{print $1}' > grub
mv grub /etc/default/grub
echo 'GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=$SCREEN_SIZE-$SCREEN_DEPTH,mtrr=3,scroll=ywrap"' >> /etc/default/grub
echo 'GRUB_GFXMODE=$SCREEN_SIZE" >> /etc/default/grub
cat /etc/initramfs-tools/modules | awk -F "uvesa" '{print $1}' > /etc/initramfs-tools/modules
echo 'uvesafb mode_option=$SCREEN_SIZE-$SCREEN_DEPTH mtrr=3 scroll=ywrap' >> /etc/initramfs-tools/modules
echo FRAMEBUFFER=y | tee /etc/initramfs-tools/conf.d/splashs
update-grub
update-initramfs -u

```
thats the script above

im now just missing how im supposed to print out the variables (right now, it just prints out SCREEN_SIZE and SCREEN_DEPTH

---

### Post by DaithiF on 2010-05-15
Hi,
to answer your question about the variables, the statements where you assign values to them won't work as they are now for 2 reasons ...
1. you have a space after the '=' sign, there can't be spaces around the equals sign when assigning values to variables in bash
2. you need to tell bash to execute the part on the right hand side of the equals sign, do this by enclosing the commands in either $(  )  or backticks ``
so:
```
SCREEN_SIZE=$(xdpyinfo | grep dimensions | awk -F "dimensions:    " '{print $2}' | awk -F " pixels" '{print $1}')
SCREEN_DEPTH=$(xdpyinfo | grep depths | awk -F ":    " '{print $2}' | awk -F ", " '{print $1}')

```The other thing I would point out is that these two lines don't do what I think you want them to do:
```
cat /etc/default/grub | sudo awk -F "GRUB_CMDLINE_LINUX_DEFAULT" '{print $1}' > grub
cat /etc/default/grub | sudo awk -F "GRUB_GFXMODE" '{print $1}' > grub

```I *think* (forgive me if I'm wrong), that you want to delete these 2 lines from the grub file because you are adding 2 replacment entries later on (?)
A bettter way to do this would be:
```
sed -i '/GRUB_CMDLINE_LINUX_DEFAULT/d' /etc/default/grub
sed -i '/GRUB_GFXMODE/d' /etc/default/grub

```And just a couple of  other suggestions:
1. the way you are using awk to pick out values by splitting lines using the -F parameter multiple times is a little ungainly imho.  I would suggest sed may be a better way.  For example, if the dimensions line from the xpdyinfo command was something like:  dimensions:     1024x768 pixels
and you wanted to pick out the 1024x768 piece then this would do it
```
(commands as before) | sed -r 's/dimensions:\s+([0-9x]+).*/\1/'

```2. no need to use cat to pipe values into awk (or sed), they can operate on files just fine themselves, so 
awk '{ some commands }' /etc/default/grub
though of course if you're stringing together multiple commands then you would pipe into awk or sed in that case.

hope this helps

---

