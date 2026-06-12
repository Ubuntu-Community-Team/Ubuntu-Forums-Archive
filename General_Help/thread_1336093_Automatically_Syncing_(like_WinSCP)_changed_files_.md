---
title: "Automatically Syncing (like WinSCP) changed files over SSH/SFTP"
date: 2009-11-24
forum: General Help
---

### Post by nomaed on 2009-11-24
Hi,

I know that this issue is not Ubuntu specific, but since I am using Ubuntu and I am quite clueless about Linux, I decided to ask here.

Anyhow, I've been searching for hours for a complete solution, but couldn't find anything.

What I need is a functionality similar to what WinSCP offers; When it detects a file change in a directory, it automatically copies the changed file(s) (through SSH or SFTP) to a remote directory.

Now, I know that I can use rsync to periodically or manually sync between my local dir and the remote one, but that's now what I am looking for.
And I also know that the kernel has file-write monitoring, but where do I find the two of them together in the same program?

I am a programmer, and I want to move my PHP development environment from Windows to Linux (on Ubuntu 9.10). There are plenty of nice editors and IDEs, and a lot of useful tools, but this issue is the only thing that's still keeping for me from switching to Ubuntu completely.

Thanks.

---

### Post by konradpiskorz on 2009-11-24
Hello Nomaed,

I am not familiar with WinSCP and might be able to help you with some clarification.

From what I understand you would like to have your php code organized on your workstation computer which is automatically uploaded to your server as you save and add new files on your workstation?  Or perhaps multiple servers behind a load balancer?

How crucial is it that it happens automatically?  You can have a sh script which scans your directory say /wwwserv  with the stat command every 5(or 3s or 2hrs whatever you like) seconds and if a change is noticed rsync can be run.  This is more efficient than running rsync all the time, although that is also an option.  You can also bind a free key on your keyboard to do this as well if you like.  It will only be a few lines of code, just depends on exactly what you want to do.

---

### Post by nomaed on 2009-11-24
Thanks for the reply, but I know I can manually or periodically run rsync (with cron or any other method).

WinSCP is an SCP client for Windows with a GUI.
It has a split interface, one side is your machine, and the other side is the remote machine.
You can click a button, and it enters "Sync mode", which means that it monitors for file changes on the local machine, and copies these changed files to the remote host.
That is, assuming that the directory structure is the same.

---

### Post by konradpiskorz on 2009-11-24
Ok, I have a better idea of what you want.

The best solution would be to install incron.  It is similar to cron except it uses inotify instead of a timer.  inotify monitors files or directories for read or write and can then run a script that would call rsync or something equivalent to transfer the file.

I think this is the solution you're looking for though I do not have experience with incron myself, it looks simple enough.

---

### Post by nomaed on 2009-11-24
That sounds pretty much what I was looking for! Thanks a lot, I'll check incron out :)

---

### Post by nomaed on 2009-11-25
Just to let anyone who might be looking for similar solution:

incron is a great service, very comfortable, but with one huge problem (I believe it will be "fixed" in the next versions):
It doesn't detect changes recursively in sub-directories.

I did find another tool that does that: lsyncd
It uses inotify to get updates, and rsync to do the syncing.
For now, it is a great solution!

---

### Post by fak3r on 2010-10-18
I have an article about using lsyncd to sync to remote systems over SSH (using key based authentication) to provide an open source dropbox -like implementation, and it works as well as you'd expect awesome commandline tools in Linux to work! :)
[http://fak3r.com/2009/09/14/howto-build-your-own-open-source-dropbox-clone/](http://fak3r.com/2009/09/14/howto-build-your-own-open-source-dropbox-clone/)

This has been a *very* popular post on my site, so I'm looking to formalize a bash based installer to at least allow for easy setup of a client/server setup with the hope that someone (Sparkleshare? [http://www.sparkleshare.org/](http://www.sparkleshare.org/)) will come up with a cross-platform UI to control it.

---

### Post by webasdf on 2010-12-07
I have the same issue.  I loved winscp "keep remote directory up to date" command.  However, in my quest to rid myself of Windows, I lost winscp.  I did write a script that uses fileschanged and rsync to do something similar much closer to real time.

How to use:

[LIST]
[*]Make sure you have fileschanged installed
[*]Save this script in /usr/local/bin/livesync or somewhere reachable in your $PATH and make it executable
[*]Use Nautilus to connect to the remote host (sftp or ftp)
[*]Run this script by doing livesync **_SOURCE_** **_DEST_**
[*]The DEST directory will be in /home/[username]/.gvfs/[path to ftp scp or whatever]
[/LIST]
A Couple downsides:
[LIST]
[*]It is slower than winscp (my guess is because it goes through Nautilus and has to detect changes through rsync as well)
[*]You have to manually create the destination directory if it doesn't already exist.  So if you're adding a directory, it won't detect and create the directory on the DEST side.
[*]Probably more that I haven't noticed yet
[*]Also, do not attempt to synchronize a SRC directory named "rsyncThis".  That would probably not be good :)
[/LIST]
```
#!/bin/sh

upload_files()
{
	if [ "$HOMEDIR" = "." ]
	then
		HOMEDIR=`pwd`
	fi

	while read  input
	do
		SYNCFILE=${input#$HOMEDIR}
		echo -n "Sync File: $SYNCFILE..."
		rsync -Cvz --temp-dir="$REMOTEDIR" "$HOMEDIR/$SYNCFILE" "$REMOTEDIR/$SYNCFILE" > /dev/null
		echo "Done."
	done
}


help()
{
	echo "Live rsync copy from one directory to another.  This will overwrite the existing files on DEST."
	echo "Usage: $0 SOURCE DEST"	
}


case "$1" in
  rsyncThis)
	HOMEDIR=$2
	REMOTEDIR=$3
	echo "HOMEDIR=$HOMEDIR"
	echo "REMOTEDIR=$REMOTEDIR"
	upload_files
	;;

  help)
	help
	;;

  *)
	if [ -n "$1" ] && [ -n "$2" ]
	then
		fileschanged -r "$1" | "$0" rsyncThis "$1" "$2"
	else
		help
	fi
	;;
esac


```

---

