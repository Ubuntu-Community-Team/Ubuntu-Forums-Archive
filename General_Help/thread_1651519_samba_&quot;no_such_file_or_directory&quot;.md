---
title: "samba: &quot;no such file or directory&quot;"
date: 2010-12-23
forum: General Help
---

### Post by outofsync on 2010-12-23
I installed samba on Maverick following "the easy way" (ie: right click on a folder with Nautilus, and then sharing it). Then samba was automatically installed, and the permissions of the shared folder were set to 777 (I checked that from the terminal).

Then I connect from an IRIX box, using smbclient. It successfully connects to the shared folder, and I can list the directory contents, as well as changing the current directory.

The problem is that I cannot read nor write any file in the shared folder. If I try to run a shell command like this:

! gunzip myfile.gz

Then I get the error "myfile.gz: No such file or directory"

Or if I try to print a file like this:

print myfile.txt

Then I get the error "Error opening local file myfile.txt" (btw, I don't understand why it says "local file", since I understand it should say "remote file").

Any ideas on what could be happening here? As I said, I checked that the shared directory permissions are set to 777.

I also tried to look at the smb.conf file, but found no entry for my shared folder... it seems ubuntu configures shared folders in another place apart from smb.conf.

TIA

---

### Post by outofsync on 2010-12-23
Ooops, I found a very strange behaviour which might help to figure out what's happening:

If I execute "ls" on smbclient, I get the listing of the shared directory, as expected.

But, if I execute "! ls" (ie: the ls command from the UNIX shell) then I get the listing of the cwd in the local machine, and not on the shared directory!!!!

Any idea of what's happening?

---

### Post by luvshines on 2010-12-23
I think 'man smbclient' has all your answers :)
```

# Snippets from man pages
! [shell command]
If shell command is specified, the ! command will execute a shell locally and run the
specified shell command. If no command is specified, a local shell will be run.

print <file name>
Print the specified file from the local machine through a printable service on the
server.
```

---

