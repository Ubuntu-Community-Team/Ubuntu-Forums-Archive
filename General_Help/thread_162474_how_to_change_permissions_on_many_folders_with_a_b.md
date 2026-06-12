---
title: "how to change permissions on many folders with a bash script?"
date: 2006-04-19
forum: General Help
---

### Post by LordMerlin on 2006-04-19
Hi guys
 

 I wonder if someone can help me with a simple batch script. For some odd reason all my user's home folder permissions have changed:
 

 drwx------    2        511 users 4096 Apr  3 12:41 tmatshazi
drwx------    2        511 users 4096 Apr  3 12:43 tmkwena
drwx------    2        511 users 4096 Apr  3 12:44 tmohajane
drwx------    2        511 users 4096 Apr  6 12:05 tmolefe
drwx------    2        511 users 4096 Apr  6 12:06 tmsimango

 

 Is there a quick and dirty way of changing each user's folder to his own?
 

 Currently running chown -R zmei zmei is going to take me ages. We have about 230 users.
 

 I was thinking of something like 
 

 for each [something goes here]
 chown -R $user $user
 

 But I don't know too much about these things.
 

 tia :)

---

### Post by kabus on 2006-04-19
Try using find with the -type argument to find all directories and -exec to run a command on each of them. Something like this should work :

```
 find . -type d -exec chmod 755 '{}' \;
```

---

### Post by souki on 2006-04-19
with perl, you can do something like this:

```
#!/usr/bin/perl
#
use strict;
my $file = "/etc/passwd";

my %bypass = ('klog'=>1, 'syslog'=> 1, 'cupsys'=>1, 'ftp'=>1);
open(FH, "<$file") || die "can't open $file : $!\n";
while( my $line=<FH> ) {
        chop($line);
        if ( $line =~ /^([^:]*):([^:]*):([^:]*):([^:]*):([^:]*):([^:]*):([^:]*)$/ ) {
                my ($login, $uid, $gid, $home, $shell) = ($1, $3, $4, $6, $7);
                next unless -d $home;
                next unless $home =~ /^\/home\/.+$/;
                next if $bypass{$login};
                print "$login, $uid, $gid, $home, $shell\n";
                #`chown -R $uid:$gid $home`;
        }
}
```

I've restricted to folders in "/home" and you can protect some folders with the %bypass variable

---

### Post by LordMerlin on 2006-04-19
Here's a quick, short one :)

[I]```

for user in * ; do
[/I][I]     chown -R $user $user
[/I]*done*


```

---

### Post by TreetopClimber on 2006-04-30
where and how is this done I have been trying to change the permissions on my /var/www folder so I can transfer files from my cdrom to this folder. It was easily done with windows 2003 server but doesnt work with linux or (ubuntu) I have made a couple inquiries already any extra help would be great, thanks in advance TT

---

### Post by MikeDestroy on 2007-08-23
try using

chmod +x [/path/folder name] to allow

"         "  -x "                                 " to disallow

---

