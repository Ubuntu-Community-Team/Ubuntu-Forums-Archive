---
title: "scp only recent files... script help"
date: 2012-02-07
forum: General Help
---

### Post by JCM_Pico on 2012-02-07
Hi there, 

I'm trying to create a bash script to copy only recent files from a remote machine... I usually loging into the machine throw ssh and copy the file name that I want to download to my computer, and than I use scp to copy it to my machine....
I would like to change this procedure by creating a bash script that only download the files meeting a certain criteria (e.g name, date, size)... is there any way of making this?

Thanks

---

### Post by Lars Noodén on 2012-02-07
Well, [find](http://manpages.ubuntu.com/manpages/oneiric/en/man1/find.1.html) can show you files matching a certain name, date, or size.  

If you a key for authentication, then Ubuntu has a key agent that you can use to avoid typing the passphrase more than once.  Here is an approximation, it will need tweaking to work:

```

# find files larger than 100KB and copy them
find /some/path -size +100k -exec scp -i /path/to/key "{}" user@remotehost.org:. \;

```

---

### Post by Khayyam on 2012-02-07
JCM_Pico ...

I would say scp is the wrong tool, rsync is really designed with this kind of task in mind. It can use ssh as the transport ('rsync -e ssh'), sync only changed files, do incremental backups, exclusions, etc, etc.

It could provide examples, but a simple google will give you some idea of how to set about using it.

HTH ...

---

### Post by JCM_Pico on 2012-02-07
> **Khayyam said:**
> JCM_Pico ...

I would say scp is the wrong tool, rsync is really designed with this kind of task in mind. It can use ssh as the transport ('rsync -e ssh'), sync only changed files, do incremental backups, exclusions, etc, etc.

It could provide examples, but a simple google will give you some idea of how to set about using it.

HTH ...

I know about rsync... but I have many files in the remote computer.... and I dont have them I my computer.... I just want to get from the remote server a file that have some atributes... like the date... every one started by A... things like that.... So rsync is not the solution... 

I'll give a try to the suggestion of Lars Noodén... its seam that is the right way.... ;)

---

### Post by Khayyam on 2012-02-08
JM_Pico ..

Somehow I read "from a" as "to a" .. that'll taught me to read propa before jumping in with advice .. heh.

Still, I think rsync can be used for your purpose. A script running on the remote machine, or run via 'ssh -c', executes 'rsync --dry-run' to check for attributes your looking for (recent changes, ownership, and what-have-you) and dumps it to a file or [inotify](http://linux.die.net/man/7/inotify) sends you its output. This can then be tagged, parsed, etc, and used as input to scp.

As 'rsync' has the ability to log and keep stats (--log-file --log-file-format --stats) it has the advantage over 'find' in that it can be configured to use these logs to "remember" prior sync's which might be useful for regular usage.

Anyhow, it depends on how much effort you want to put into writting your script, the example from Lars is probably exactly what your looking for, so enough from me ..

best ...

---

### Post by JCM_Pico on 2012-02-08
> **Khayyam said:**
> JM_Pico ..

Somehow I read "from a" as "to a" .. that'll taught me to read propa before jumping in with advice .. heh.

Still, I think rsync can be used for your purpose. A script running on the remote machine, or run via 'ssh -c', executes 'rsync --dry-run' to check for attributes your looking for (recent changes, ownership, and what-have-you) and dumps it to a file or [inotify]("http://linux.die.net/man/7/inotify") sends you its output. This can then be tagged, parsed, etc, and used as input to scp.

As 'rsync' has the ability to log and keep stats (--log-file --log-file-format --stats) it has the advantage over 'find' in that it can be configured to use these logs to "remember" prior sync's which might be useful for regular usage.

Anyhow, it depends on how much effort you want to put into writting your script, the example from Lars is probably exactly what your looking for, so enough from me ..

best ...


I liked the way you think :)... This way I'll learn more.....
I'm not familiarized with inotify can you explain me some more about the procedure....

What I understand is to create a a dry run with rsync - this will tell me the files that are in the remote computer folder.... then I can use "something?" to identify the file that I want and then use scp  to copy it... right?

---

### Post by jamesisin on 2012-02-08
You can use rsync in either direction.  The basic format would be thus:

```
rsync -arguments --more-arguments user@remoteA:/path/to/source/folder/or/file(s) user@remoteB:/path/to/source/folder/or/file(s)
```

Depending on permissions sudo may be used/required.  (If they username is the same across systems user@ may be omitted.)

Oh, and using rsync is much better than using scp because rsync checks its work.

---

### Post by Khayyam on 2012-02-08
> **JCM_Pico said:**
> [...]I'm not familiarized with inotify can you explain me some more about the procedure...

Well, [inotify](http://inotify.aiken.cz/?section=inotify&page=about&lang=en) is an (in kernel) "filesystem notification technology" that "provides [the] possibility [to] monitor various events on files in filesystems". Applications (like rsync) can make use of it for gauging when they should perform back-ups, etc.

The link I provided previously was a mistake I'd ment to link to [rsync-inotify](http://code.google.com/p/rsync-inotify/) but had inserted the link to the manpage instead (the links provided in this post should give you a better idea of what inotify can do). I was also a little vague stating how it might tie into your "script", the examples on the the [inotify-tools wiki](https://github.com/rvoicilas/inotify-tools/wiki/) provide some good examples. What I'd intended to say was, your script (or some combination of scripts, rsync, and "glue") could monitor (via inotify) the filesystem, run, provide a report on changes and (ultimately) provide you with a "list" of files to pass to 'scp'. Most of this seems doable, but as I said it'll take some work to pull it together.

> **JCM_Pico said:**
> What I understand is to create a a dry run with rsync - this will tell me the files that are in the remote computer folder.... then I can use "something?" to identify the file that I want and then use scp  to copy it... right?

rsync-inotify (or a tool similar to those provided on the inotify-tools wiki) monitors for a change in filesystem, it then carrys out a task, 'rsync --dry-run for example, and a creates a report of file changes, this is then dumped in a file and/or emailed to you. A seperate script on you client machine parses this file and either passes the list to scp or prompts you for input "Download: /files/newfile.txt [yes|no]?".

As this is scripted there are any number of additional steps that could be included, its just a matter of gluing them together.

The only assumption I'm making is that the remote host runs Linux and is running a kernel with inotify enabled.

HTH ..

---

### Post by Lars Noodén on 2012-02-08
> **jamesisin said:**
> 
```
rsync -arguments --more-arguments user@remoteA:/path/to/source/folder/or/file(s) user@remoteB:/path/to/source/folder/or/file(s)
```


It'd be really cool if both could be remote but the source and destination cannot both be remote.  Just one or the other or both local.  A work-around might be to go via SSHFS for one or both of them.

---

### Post by jamesisin on 2012-02-08
It's true: when using rsync by itself *either* the source *or* the destination must be local (and either can be remote), but they cannot *both* be remote.  If you want to do a remote-to-remote sync then you can ssh into one of those systems.  (I showed both as remote just to display how each syntax would appear.)

---

### Post by SeijiSensei on 2012-02-08
As much as I use the command prompt for nearly everything, selecting files by name, date, etc., is often much easier with a GUI file manager.  In KDE, I can mount a remote machine via SSH using something called the "[fish]("http://en.wikipedia.org/wiki/Files_transferred_over_shell_protocol")" protocol.  (Using the dolphin file manager, you just type a fish URL like "fish://server/," and it will create an SSH connection to the server.)  Apparently the text-based Midnight Commander application has the same ability.  I can't find any evidence that this is supported by GNOME, though.

Another option is to use NFS to export the directory from the server and mount it on the local machine.  NFS is an insecure protocol though, so I'd only use it over an SSH or OpenVPN tunnel.

---

### Post by JCM_Pico on 2012-02-08
> **jamesisin said:**
> You can use rsync in either direction.  The basic format would be thus:

```
rsync -arguments --more-arguments user@remoteA:/path/to/source/folder/or/file(s) user@remoteB:/path/to/source/folder/or/file(s)
```Depending on permissions sudo may be used/required.  (If they username is the same across systems user@ may be omitted.)

Oh, and using rsync is much better than using scp because rsync checks its work.

Imagine having a folder in a remote computer that is like your trunk.... where you have some large files that you don't need in you personal laptop... and sometimes you use that computer to make some large downloads, so that yours don't have to be all night long running.... if you want just the last download you made you will not run rsync with some arguments.... because it will download the all folder to your pc...

Now imagine if you have a script, or something, that will only download the files created in 08/12/2011... or the files larger then 1 Gb.... or the files that have "hello" in their names....   It's that what I'm looking for.....

Lars Noodén and SeijiSensei nice idea I could run sshfs to mount the folder in my system... but I like challenges :D

I'll try to follow Khayyam idea :P

---

### Post by Khayyam on 2012-02-09
JCM_Pico ...

I'm inclined to agree with Lars & SeijiSensi, sshfs mounting is probably a better option. Using your "trunk" analogy, with sshfs you simply open the trunk, with scp you have to scp the content of the trunk to the dresser to get to your underware. You could still use inotify-rsync and such to create reports of changes but scp'ing the files doesn't really serve any purpose, unless they are to be accessed when there is no network available.

I've found sshfs to be pretty sturdy .. accessing highres H.264/Matroska without jitters connecting to a server ITA over ADSL.

Anyhow .. worth keeping in mind.

best .. k

---

### Post by jamesisin on 2012-02-10
Anything you can do using scp you can do using rsync.  I run rsync on single files (where the source would then be [email]user@machine:/path/to/file.ext[/email]) all the time.  Combine it with something like find and you have pretty much unlimited regex flexibility available.  And rsync checks its work.

---

### Post by Khayyam on 2012-02-10
jamesisin ...

Actually rsync will not only do what scp can do, it'll do it better. With a broken transfer rsync will sync only those parts of the file that are missing, scp will re-transfer the file in toto. This is one of the advantages of its "checks".

Rsync also tends to perform better:

```
rsync  -aze  'ssh'  RunTime:  System:  3.90;   User:  15.54;  Elapsed:0:48.96 :  
rsync  -ae   'ssh'  RunTime:  System:  12.61;  User:  47.56;  Elapsed:1:49.80 :  
scp    -r    ...    RunTime:  System:  11.69;  User:  41.92;  Elapsed:2:03.16 :  
rsync  -az   ...    RunTime:  System:  4.02;   User:  15.52;  Elapsed:0:47.11 :  
rsync  -a    ...    RunTime:  System:  12.69;  User:  47.53;  Elapsed:1:55.53 : 
```It does have its pitfalls, its syntax can often catch people unawares ("trailing slashes" etc). Regardless of any protential pitfalls I'd say it not only does everything scp can do, but does them better.

best ...

---

### Post by Lars Noodén on 2012-02-10
> **JCM_Pico said:**
> ...

Now imagine if you have a script, or something, that will only download the files created in 08/12/2011... or the files larger then 1 Gb.... or the files that have "hello" in their names....   It's that what I'm looking for.....

rsync can match by file name, but for matching a certain size or creation date, that will have to be find.

---

### Post by Khayyam on 2012-02-10
> **Lars Noodén said:**
> rsync can match by file name, but for matching a certain size or creation date, that will have to be find.

Lars ...

Yes, but find can be incorporated using rsync's 'files-from=' so its not a huge drawback.

```
#/bin/bash

ssh user@host "find /path -size +100M -newermt "Jan 01, 2012" > filelist.out" &&
scp user@host:filelist.out filelist.in &&
rsync -av --files-from=filelist.in source:/ dest
```Similarly for a local sync, only this time we pipe stdout to '--files-from='

```
find . -size +100M -newermt "Jan 01, 2012" -print0 | rsync -av --files-from=- --from0 ./ ./dest/
```I'm sure there are probably otherways to do this (from the client to the server ... '-exec rsync -av { } dest' or what-have-you), but as we're rsync'ing files on the server to the client, using '--files-from=' may be the best way to incorporate find's capabilitites into rsync.
     
best ..

---

### Post by Lars Noodén on 2012-02-10
> **Khayyam said:**
> 
Yes, but find can be incorporated using rsync's 'files-from=' so its not a huge drawback.

Clever!  I'd never tried rsync that way, but it works.

---

### Post by JCM_Pico on 2012-02-10
> **Khayyam said:**
> Lars ...

Yes, but find can be incorporated using rsync's 'files-from=' so its not a huge drawback.

```
#/bin/bash

ssh user@host "find /path -size +100M -newermt "Jan 01, 2012" > filelist.out" &&
scp user@host:filelist.out filelist.in &&
rsync -av --files-from=filelist.in source:/path dest
```Similarly for a local sync, only this time we pipe stdout to '--files-from='

```
find . -size +100M -newermt "Jan 01, 2012" -print0 | rsync -av --files-from=- --from0 ./ ./dest/
```I'm sure there are probably otherways to do this (from the client to the server ... '-exec rsync -av { } dest' or what-have-you), but as we're rsync'ing files on the server to the client, using '--files-from=' may be the best way to incorporate find's capabilitites into rsync.
     
best ..


Great idea... but can't make it work.... 
In rsync when you say source:/path I should replace with user@host:/path... right... if this is the case... in the file.in there will be the full path to the file.... when rsync reads that file it will try to download [email]user@host:/path/path_in_filelist.in[/email] --> therefore it fails....
Can't run it by just writing:
```
rsync -av --files-from=filelist.in source: dest
```
Neither 
```
rsync -av --files-from=filelist.in source dest
```

Any idea?

---

### Post by Khayyam on 2012-02-10
> **JCM_Pico said:**
> Great idea ... but can't make it work ...

In rsync when you say source:/path I should replace with user@host:/path... right... if this is the case... in the file.in there will be the full path to the file.... when rsync reads that file it will try to download [EMAIL="user@host:/path/path_in_filelist.in"]:[COLOR=Black]/path/path_in_filelist.in[/COLOR][/EMAIL] --> therefore it fails

Actually, no, I should have omited the 'path' bit (corrected above) .. all that is needed is a slash. I just tested it here and the following works as expected.

```
rsync -av --files-from=filelist.in source:/ dest
```

Sorry about that, I'm just used to stipulating :/path in examples .. my bad.

best ...

---

### Post by jamesisin on 2012-02-10
What they said.

---

### Post by JCM_Pico on 2012-02-10
Well.... This Thread seems to be SOLVED :D 

Thank you a lot for all the suggestions and the help given

---

### Post by Khayyam on 2012-02-11
> **JCM_Pico said:**
> Well ... This Thread seems to be SOLVED ... Thank you a lot for all the suggestions and the help given

Your welcome ... no doubt there are ways the above script could be improved. I would probably make the values passed to 'find' variables so these could be adjusted via the command line (rather than editing the script). I'd also add some clean-up commands to remove, or archive, filelist.*

Anyhow, good to hear that its working for you ..

best .. khay

---

### Post by JCM_Pico on 2012-02-12
I worked the script around, making it possibel to allow user input from the command shell and made it remove the unnecessary files.... :D

---

### Post by Khayyam on 2012-02-12
> **JCM_Pico said:**
> I worked the script around, making it possibel to allow user input from the command shell and made it remove the unnecessary files.

In which case it might be worth while posting it here in a codeblock and/or as an attatchment. There maybe others who could use it. Obviously remove/edit anything relating to your user/hosts.

Had I written "distributed under the GPL version 2" you'd have my lawyers on you .. heheh.

best .. khay

---

### Post by JCM_Pico on 2012-02-12
This is the final script....

1 - I added a key to the key agent in order to avoid entering the password 3 times....

Create the key:
```
$ ssh-keygen -t rsa
```

This will prompt you for a location to save the keys, and a pass-phrase:

```
Generating public/private rsa key pair. Enter file in which to save the key (/home/user/.ssh/id_rsa):  Enter passphrase (empty for no passphrase):  Enter same passphrase again:  Your identification has been saved in /home/user/.ssh/id_rsa. Your public key has been saved in /home/user/.ssh/id_rsa.pub.
``` 

Assuming that you wish to login to the machine called mystery from your current host with the id_rsa and id_rsa.pub files you've just generated you should run the following command:


```

ssh-copy-id -i ~/.ssh/id_rsa.pub username@mystery
```


More info about this procedure can be found at [http://www.debian-administration.org/articles/152](http://www.debian-administration.org/articles/152) . Also its were I got the info to post here.... :D


2 -  Simple changes in the script done by Khayyam


```



#/bin/bash


#Script to copy files from remote host
#Distributed under the GPL version 2 =)



date=$1
fsize=$2


if [ $# -lt 2 ]; then
  echo "Usage: $0 <date(yyyy-mm-dd)> <file bigger then (x)>"
  exit 1
fi

ssh -i /home/user/.ssh/id_rsa username@mystery "find /path -size +$fsizeM -newermt "$date" > filelist.out" &&

scp -i /home/user/.ssh/id_rsa username@mystery:filelist.out filelist.in &&

rsync -avuzh --progress --files-from=filelist.in  username@mystery:/ /dest


read -p "Remove filelist.in (yes/no): " RESPONSE

if [ "$RESPONSE" = yes ] ; then
   rm filelist.in
   echo "filelist.in removed!"
else
   echo "ilelist.in NOT removed!"
fi



```

---

### Post by Khayyam on 2012-02-12
JCM_Pico ..

Hmmmm ... all args to find can be passed via the command line with something like this:

```
#!/bin/bash

if [[ -z "$#" ]]; then
    echo "This scripts expects 'file' type options"
    echo "Usage: $(basename $0) /path options"
    exit 1
fi

FARGS="$@"

find ${FARGS}
```This  is is just a wrapper for find, but it would work similarly with the  your script. Doing it this way means you can use all of find features,  and not simply those defined in the script.

You could also set  variables for ${DEST}, ${KEEP_LIST}, ${FILE_LIST}, etc, with default  values, eg: KEEP_LIST=${KEEP_LIST:-no} DEST=${DEST:-$HOME/},  FILE_LIST=${FILE_LIST:-filelist-$(date +%F)}. This way you can change them on the  fly, define them in your .bash_profile, or have it use the defaults (the  'defaults' are on the right side of the variable).

```
if [[ ${KEEP_LIST} = "yes" ]]; then
    mv filelist.in filelist-$(date +%F).in
else
    rm filelist.in
fi
```Some other issues:

There is no "#!" .. your missing the bang.

You don't need to use the "ssh -i", "~/ssh/id_rsa (or id_dsa) are the default.

Variables  should be in currly braces, +$fsizeM for instance, should be  +${FSIZE}M, how is the shell to know that you mean the 'M' to be outside  the variable. Also, I always capitalise variables.

These are just some suggestions, your probably OK with it as it is so I'll leave it at that

best ... khay

---

### Post by JCM_Pico on 2012-02-13
> **Khayyam said:**
> JCM_Pico ..

Hmmmm ... 

...

best ... khay

Thanks for the scripting tips :D 
Its allways good to learn good things 

cheers

---

