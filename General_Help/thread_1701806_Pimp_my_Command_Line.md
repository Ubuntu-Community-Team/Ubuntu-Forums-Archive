---
title: "Pimp my Command Line"
date: 2011-03-06
forum: General Help
---

### Post by jon.reeve on 2011-03-06
So I used Arch linux for a while and was really impressed and how colorful the commandline output was. Not only from ls, which I was able to emulate by adding "alias ls="ls --color"" to my .bashrc, but also during, say, bootup and other times. 

Anyway, I was just wondering, what tricks do you guys use to make your command line experience more visually appealing? Fonts, colors, hacks, terminal profiles?

---

### Post by anirudhtomer on 2011-03-06
I prefer to create aliases for the commands I use the most. "reset" being one of  them.

Apart from that I create shell scripts and save them in my /usr/bin folder. Actually this helps a lot.

You can also use [cowsay and fortune]("http://en.wikipedia.org/wiki/Cowsay") to add spice to your terminal. Check out this link as well: [http://systemsdaemon.blogspot.com/2011/01/make-your-linux-gnome-terminal-look.html](http://systemsdaemon.blogspot.com/2011/01/make-your-linux-gnome-terminal-look.html)

---

### Post by Rushyang on 2011-03-07
Well, I kept nice apple logo in the background which is in violet color.. But here are some of my settings for using terminal..
1) I created some aliases for my frequent used directories and commands.
2) Especially alias of xclip is great, which I use to copy terminal output to my clipboard OR taking a clipboard's output to the terminal...
> 
echo "This is line to be forwarded into clipboard" | xclip -selection clipboard
xclip -selection clipboard -o

for `xclip -selection clipboard` I have created alias "copy" and for `xclip -selection clipboard -o`, "paste" into my .bashrc file.

3) I use to take back up of my ~/.bash_history file.. Though I have increased histline limit to..
HISTSIZE=100000
HISTFILESIZE=200000
and saved in my .bashrc file.. But, I also take back up of .bash_history through a [bash script]("http://paste.ubuntu.com/576808/") I created and call it through a alias I named into .bashrc.. which later, I just created a cronjob for it.

4) I also changed some PS1 settings in .bashrc file.. so that terminal would display only current working directory.. instead of that whole path.

---

### Post by slooksterpsv on 2011-03-07
I create scripts to simplify process I do every day using bash and python, examples:

1. Backup my LG Optimus S Android phone and make sure that I'm not copying duplicate files.
2. Backup new files from my computer to my external.
3. Backup modified files from my computer to my external - in case I write a document back it up change document and the backup new files doesn't copy the newer file.
4. Delete old files from my external that are no longer on (or moved) from my computer.
5. Create an ISO of my current file system

Here's those scripts just for fun:

```

#Backup new files
for file in *; do
	cp -Rn "$file" /media/FreeAgent\ Drive/
	echo "Done with directory $file"
done

```
```

#Update modified files on backup
import os

rootpath = "/home/shawn"
destpath = "/media/FreeAgent Drive"
destcppath = "/media/FreeAgent Drive"
sl = "/"

def getList(dir):
	tdx = []
	tdy = []
	tall = []
	skip = 0
	try:
		tall = os.listdir(dir)
	except Exception as inst:
		print "Exception processing " + dir
		skip = 1

	if skip == 0:
		for a in tall:
			if os.path.isdir(dir + sl + a):
				if os.path.islink(dir + sl + a):
					pass
				else:
					tdx.append(dir + sl + a)
			elif os.path.isfile(dir + sl + a):
				if os.path.islink(dir + sl + a):
					pass
				else:
					tdy.append(dir + sl + a)
			else:
				1 + 1
		return tdx, tdy
	else:
		return 0, 0

def checkMod(fil):
	filpath = fil[len(rootpath):len(fil)]
	if filpath[len(filpath)-1:len(filpath)] == "/":
		print "/"
	else:
		pass
	if os.path.exists(destpath + filpath):
		if os.path.getmtime(fil) > os.path.getmtime(destpath + filpath):
			print fil
			os.system("cp \"" + fil + "\" \"" + destcppath + filpath + "\"")
		else:
			pass
	else:
		if os.path.islink(destpath + filpath):
			pass
		else:
			print destpath + filpath + " doesn't exist!"
			os.system("cp \"" + fil + "\" \"" + destcppath + filpath + "\"")

def process(dir):
	dirdx,filex = getList(dir)
	if dirdx == 0 and filex == 0:
		pass
	else:
		for b in filex:
			checkMod(b)
		for a in dirdx:
			process(a)
if os.path.exists(destpath):
	adir,afile = getList(rootpath)

	for a in adir:
		process(a)
else:
	print "Please Connect FreeAgent Drive First!"

```
```

#Remove files from backup that no longer exist or were moved
import os

destpath = "/home/shawn"
rootpath = "/media/FreeAgent Drive"
sl = "/"

def getList(dir):
	tdx = []
	tdy = []
	tall = []
	skip = 0
	try:
		tall = os.listdir(dir)
	except Exception as inst:
		print "Exception processing " + dir
		skip = 1
	
	if skip == 0:
		for a in tall:
			if os.path.isdir(dir + sl + a):
				if os.path.islink(dir + sl + a):
					pass
				else:
					tdx.append(dir + sl + a)
			elif os.path.isfile(dir + sl + a):
				if os.path.islink(dir + sl + a):
					pass
				else:
					tdy.append(dir + sl + a)
			else:
				pass
		return tdx, tdy
	else:
		return 0, 0

def checkMod(fil):
	filpath = fil[len(rootpath):len(fil)]
	if not os.path.exists(destpath + filpath):
		#if os.path.getmtime(fil) > os.path.getmtime(destpath + filpath):
		#	print fil
		#	os.system("cp \"" + fil + "\" \"" + destcppath + filpath + "\"")
		#else:
		#	pass
		print "Deleting " + filpath
		os.system("mv \"" + fil + "\" \"" + rootpath + "/tmp/\"")
	else:
		pass
		#if os.path.islink(destpath + filpath):
		#	pass
		#else:
		#	print destpath + filpath + " doesn't exist!"
		#	os.system("cp \"" + fil + "\" \"" + destcppath + filpath + "\"")

def process(dir):
	dirdx,filex = getList(dir)
	if dirdx == 0 and filex == 0:
		pass
	else:
		for b in filex:
			checkMod(b)
		for a in dirdx:
			process(a)

if os.path.exists(rootpath):
	adir,afile = getList(rootpath)

	for a in adir:
		process(a)
else:
	print "Please Connect FreeAgent Drive First!"

```
```

#Create ISO of current system using remastersys
import time
import os,sys
from datetime import date

additexcl = ""
argc = 0

print "Generating Configuration Files"
print "Parsing Additional Exclusional Directories: "
for arg in sys.argv:
	argc += 1
	if argc >= 2:
		additexcl += " " + arg
		print arg
print "Done!"

iso_workdir = "/home/remastersys"
iso_excludes = "/home/shawn/" + additexcl
iso_liveuser = "smint"
iso_livecdlabel = "Mint Backup"
iso_customiso = "Linux-Mint-"
iso_livecdurl = "http://www.geekconnection.org/remastersys"

today = date.today()
if today.month > 9:
	iso_customiso += str(today.month)
	iso_livecdlabel += " " + str(today.month)
else:
	iso_customiso += "0" + str(today.month)
	iso_livecdlabel += " 0" + str(today.month)

if today.day > 9:
	iso_customiso += str(today.day)
	iso_livecdlabel += " " + str(today.day)
else:
	iso_customiso += "0" + str(today.day)
	iso_livecdlabel += " 0" + str(today.day)

iso_customiso += str(today.year) + ".iso"
iso_livecdlabel += " " + str(today.year)

#Generate Configuration File
f = open("_remastersys.conf", "w")
f.write("WORKDIR=\"" + iso_workdir + "\"\n")
f.write("EXCLUDES=\"" + iso_excludes + "\"\n")
f.write("LIVEUSER=\"" + iso_liveuser + "\"\n")
f.write("LIVECDLABEL=\"" + iso_livecdlabel + "\"\n")
f.write("CUSTOMISO=\"" + iso_customiso + "\"\n")
f.write("LIVECDURL=\"" + iso_livecdurl + "\"\n")
f.write("#Created by UpdateISO.py by shawn")
f.close()

os.system("sudo rm -R /home/remastersys")
os.system("sudo mv _remastersys.conf /etc/remastersys.conf")
os.system("sudo remastersys dist && sudo mv /home/remastersys/remastersys/" + iso_customiso + " /home/shawn/Downloads/ISO/ && sudo chown shawn:shawn /home/shawn/Downloads/ISO/" + iso_customiso + "")

```
```

#Script to run the create iso, backup, etc.
import os,sys

print "==\tSTK Automated Backup\t=="

choice = ""

while str(choice).lower != "q":
	print "Please select an option for what you would like to do:\n"
	print "1) Backup files to Backup Drive"
	print "2) Backup your LG Phone Pics and Videos"
	print "3) Create an ISO of your current filesystem"
	print "Q) Quit"

	choice = str(raw_input("(1, 2, 3, Q): "))
	if choice == "1":
		if os.path.exists("/media/FreeAgent Drive/"):
			os.system("cp /home/shawn/Backup\ Utilities/UpdateBackup.sh /home/shawn/")
			os.chdir("/home/shawn/")
			os.system("./UpdateBackup.sh && rm ./UpdateBackup.sh")
			print "\n\n\n\n\nDone with Backup!\n"
		else:
			os.chdir("/home/shawn/")
			print "FreeAgent Drive not connected!"
	elif choice == "2":
		os.system("/home/shawn/Backup\ Utilities/BackupLG.sh")
	elif choice == "3":
		items = str(raw_input("Type in directories you want to exclude from the ISO\nPut a space between different directories (e.g. /home /etc):\n"))
		os.system("python /home/shawn/Backup\ Utilities/UpdateISO.py " + items + "")
		print "Done creating ISO"
	elif choice.lower() == "q":
		break
	else:
		print choice + " is not a valid selection!"

print "Thank you!"

```

---

### Post by Habitual on 2011-03-07
Thanks Shawn for the pimpin' Remastersys code.

+1

---

### Post by aeiah on 2011-03-07
this is my terminal, running dvtm inside urxvt
[[img]http://ompldr.org/tN3BkZA[/img]](http://ompldr.org/vN3BkZA)

.Xdefaults (colours, urxvt options, such as tabs):
```


urxvt.perl-ext-common:default,tabbedex

URxvt*font: xft:DejaVu Sans Mono:antialias=true:pixelsize=11
URxvt*boldFont: xft:DejaVu Sans Mono:style=bold:antialias=true:pixelsize=11
URxvt*italicFont: xft:DejaVu Sans Mono:style=italic:antialias=true:pixelsize=11
URxvt*boldItalicFont: xft:DejaVu Sans Mono:style=bolditalic:antialias=true:pixelsize=11



urxvt*termName:         rxvt
urxvt*background:       #212629
urxvt*foreground:       #656e72
urxvt*scrollBar:        false
urxvt*matcher.button:   1
urxvt*cursorBlink:      true
urxvt*cursorColor:      #719e6b
!#b1b6c8
urxvt*colorBD:          #857672

urxvt.transparent:      false
urxvt*allow_bold:       true

Xft.dpi:                96
Xft.antialias:          true
Xft.hinting:            true
Xft.hintstyle:          hintslight
Xft.rgba: 		rgb

URxvt*inheritPixmap:    false
!URxvt*tintColor:       black
!URxvt*shading:         80
URxvt*geometry:        90x31


URxvt.tabbed.tabbar-fg: 3
URxvt.tabbed.tabbar-bg: 0
URxvt.tabbed.tab-fg:    4
URxvt.tabbed.tab-bg:    0
URxvt.tabbed.title: no
URxvt.tabbed.autohide:  yes

URxvt.saveLines:	8192
URxvt*iconFile:            /home/satsuma/.icons/Meliae/scalable/apps/terminal.png

!black
URxvt*color0:           #1d1e1f
URxvt*color8:           #424446
!red
URxvt*color1:           #9e6b71
URxvt*color9:           #b69094
!green
URxvt*color2:           #547550
!#719e6b
URxvt*color10:          #94b690

!yellow
URxvt*color3:           #9e986c
URxvt*color11:          #b5b18f
!blue
URxvt*color4:           #6c8b9e
URxvt*color12:          #90a7b6
!magenta
URxvt*color5:           #986b9e
URxvt*color13:          #b290b6
!cyan
URxvt*color6:           #6b9e98
URxvt*color14:          #90b6b3
!white
URxvt*color7:           #b8baba
URxvt*color15:          #cdcfce
```



some .bashrc bits, aliases etc
```

function cyan_red_prompt
{
        local CYAN="\[\033[0;36m\]"
        local GRAY="\[\033[0;37m\]"
        local RED="\[\033[0;31m\]"
        local BLACK="\[\033[0m\]"

        PS1="${CYAN}[\h ${RED}\w${CYAN}] ${BLACK}"
}

cyan_red_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}[\h] \w\a\]$PS1"
    ;;
*)
    ;;
esac


alias alive='ps -ef|grep -v grep|grep -i '
alias network='sudo nmap -sP -oG - 192.168.1.1/24'


function down () {
links -dump downforeveryoneorjustme.com/$@ | head -n 1
}

```

---

