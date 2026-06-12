---
title: "How can i take ownership"
date: 2011-01-19
forum: General Help
---

### Post by BrendanDM on 2011-01-19
I there, I just switched to Ubuntu today and found that in some cases, I need to take ownership for files in order for them to run. So far I've tried a few ways to try to take ownership of some random executable I had on one of my flash drives, and so far have had no luck. Every time I go through the process using the terminal, and checking the file, it seems like it didn't work. At one point I used "sudo su chown /media/My\ Passport\filename.exe", and even used "sudo su chown admin:admin /media/My\ Passport\filename.exe" to try to bump the file down from being in the root group. I already switched the user I'm using to the root group, but everytime I try to bump the file down, it stays the same and won't let me select "allow executing as a program" in the permissions menu. Does anyone know of any strategies that I could use to let me take ownership of the file? Also, I have already tried copying it to my desktop, and home folders, and still nothing. Any help is appreciated, and thanks is advance.

---

### Post by slooksterpsv on 2011-01-19
For files that are EXE's you have to run those with WINE.

You can install Wine from the Software Center, or via terminal with:
sudo apt-get install wine

Once Wine is installed, you can execute the program with:
wine /path/to/program/program.exe

or:
right-click on file -> properties -> Permissions tab -> click on Allow executing file as a program.

Either way it requires WINE, and not all programs will work under wine, you can usually find out if their compatible or if you need to modify something via googling:
wine <program name>

---

### Post by Morbius1 on 2011-01-19
> At one point I used "sudo su chown /media/My\ Passport\filename.exe",  and even used "sudo su chown admin:admin /media/My\  Passport\filename.exe" to try to bump the file down from being in the  root group. I already switched the user I'm using to the root group, but  everytime I try to bump the file down, it stays the same and won't let  me select "allow executing as a program" in the permissions menu.There are a couple of issues here.

[1] Your "filename.exe" file on "My Passport" is most likely on an NTFS or Fat32 partition. Linux can't change ownership or permissions on a windows filysystem other than with a mount or an entry in fstab and it would apply to the entire partition not just a specific file.

[2] If you're using wine as slooksterpsv suggested you're still going to have a problem though because the default wine association with an "exe" file insists on checking to see if the file is executable.

Wine doesn't care if the file is executable. The problem is with something called "cautious-launcher" that is slapped on the wine ( and java ) association which checks to see if it's executable.

You've got a couple of options:

[a] Run it from the terminal as slooksterpsv suggested:
wine "/media/My\  Passport\filename.exe"

[b] Create your own wine association that doesn't have "cautious-launcher":

Right click an *.exe file > Properties  -> Open With -> Add -> Use a custom command > Then type in:  wine

Back in the "Open With" tab mark the "wine" [COLOR=#0000ff]you just added[/COLOR] as the default.

---

### Post by BrendanDM on 2011-01-19
I see. However, when I looked up wine, it said that it wasn't available on an i386 system. Are there any other programs that will allow me to run executables?

---

### Post by engine on 2011-01-24
> **Morbius1 said:**
> There are a couple of issues here.

[...] The problem is with something called "cautious-launcher" that is slapped on the wine ( and java ) association which checks to see if it's executable. [...]

Run it from the terminal as slooksterpsv suggested:
wine "/media/My\  Passport\filename.exe"


Just the tip I needed &#8210; thanks!

---

