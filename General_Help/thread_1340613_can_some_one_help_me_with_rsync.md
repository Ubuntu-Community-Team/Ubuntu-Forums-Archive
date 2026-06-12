---
title: "can some one help me with rsync?"
date: 2009-11-28
forum: General Help
---

### Post by onesojourner on 2009-11-28
I have been trying to read up on rsync but I think it is a bit over my head. I am trying sync my mp3s and my pictures between my laptop and my desktop. I would like the files to sync any time I turn my laptop on, while on my home network. 

This is what I want for my pictures for example

Desktop
/3storage/pictures

to
laptop
/1storage/pictures

from reading it sounds like I need to set up some ssh stuff?? Anyways as you can tell I am totally lost so any help is appreciated. 


Also does rsync have the ability to only back up certain file types? for example could it ignore the flac files on my desktop and only back up the mp3s?

---

### Post by XCan on 2009-11-29
First of all, do you know how to setup ssh and secure it? You will need to use a keyfile unless you fancy typing in your password on the remote machine everytime on boot. Once ssh is properly setup, using rsync with it is easy enough, the below shows the command ignoring .flac files

```

rsync -avz --delete --rsh="ssh -p22 -i /path/to/your/ssh/keyfile" --exlude=*.flac user@remote.machine.ip:/3storage/music /1storage/music 
```

---

### Post by sgosnell on 2009-11-29
You can install grsync and get a gui interface, with saved profiles, which can be easier to configure if you're used to gui's.  You can also set up a script for rsync, and set it to run at every boot through System/Preferences/Startup Programs.

---

### Post by onesojourner on 2009-11-29
I have looked at it but it does not seem as powerful as rsync and it still seems to heve a learning curve.

I think I have set up ssh, but I am not sure how to go about testing it. then will I need to run the command you gave me from the desktop or the laptop? Sorry for the dumb questions.

if it helps the local ip of the desktop is 192.168.1.146 and the laptop is 192.168.1.120

---

### Post by sgosnell on 2009-11-30
If you're saying you looked at grsync, then that is rsync, just with a GUI frontend.  If you're talking about something else, sorry but I'm lost.

---

### Post by XCan on 2009-11-30
> **onesojourner said:**
> I have looked at it but it does not seem as powerful as rsync and it still seems to heve a learning curve.

I think I have set up ssh, but I am not sure how to go about testing it. then will I need to run the command you gave me from the desktop or the laptop? Sorry for the dumb questions.

if it helps the local ip of the desktop is 192.168.1.146 and the laptop is 192.168.1.120

If you have setup ssh on your desktop you can try it out by trying to ssh into the machine by ```
 ssh 192.168.1.146 
``` 

If you can login with that, then you should be able to run the rsync command above from your laptop with
```
 
rsync -avz --delete --rsh="ssh -p22 -i /path/to/your/ssh/keyfile" --exlude=*.flac user@192.168.1.146:/3storage/music /1storage/music

```

You can of course also setup ssh on your laptop and reverse the command, the only thing rsync cares about is that it can communicate with the source and destination, i.e., ```
 rsync -avz src.location dest.location 
```

---

### Post by onesojourner on 2009-11-30
alright well apparently I  don't have it set up correctly. I will do some more reading to see what I have messed up.

---

### Post by Buggin on 2009-11-30
you probably missed teh key file he was reffering to

use this script [here]("http://www.seanodonnell.com/code/?id=68") to set up the ssh key login automatically

then it will log in with no password... you just have to tell it where tht key file is (the script will tell you where it's going... ~/.ssh/autoirized_keys i think it is) you just have to fill in teh remote host name variable

---

### Post by onesojourner on 2009-12-02
hmmm looks like that says that I need to be able to log in manually before I use the script.

```
#!/bin/sh
###########################################################
#
# file: ssh-keygen.sh
#
# Use this simple shell script to generate your
# public rsa/dsa (SSH) encryption keys, and then 
# copy the public keys to the remote machine in which
# you wish to create a 'trusted' authentication mechanism.
#
# The idea behind this authentication mechanism is to 
# allow you to login to a remote ssh server without being
# prompted for your password.
#
###########################################################
#
# :: U S A G E : I N S T R U C T I O N S ::
#
# In order for this script to work correctly, you should
# 1st manually log-in to the remote SSH server.
#
# [user@pc1] $ ssh pc2.domain.ext
#
# Once logged-in to the remote SSH server, ensure 
# that the '~/.ssh' directory exists, and has the 
# correct permissions (0700).
#
# [user@pc2] $ ls -la ~ | grep ssh
#
# If the '~/.ssh' directory DOES exist, but does not have 
# the correct permissions (drwx------), you will need to 
# execute the following command: 
#
# [user@pc2] $ chmod 0700 ~/.ssh; logout;
#
# If the '~/.ssh' directory DOES NOT exist, you will need 
# to execute the following command: 
#
# [user@pc2] $ mkdir -m 0700 ~/.ssh; logout;
#
# Now you can execute this script from your local machine.
#
# [user@pc1] $ ./ssh-keygen.sh
#
###########################################################
#
# Sean O'Donnell <sean@seanodonnell.com>
# copyleft (<) 2005, 2007 seanodonnell.com
#

SSHSERV=myusername@mysshserver.com
SSHPORT=22
SSHDIR=~/.ssh
SSHDIR_REMOTE=.ssh
TMPDIR=~

#
# function: generate_keys
# descript: Generate RSA/DSA Encryption keys using ssh-keygen
#
function generate_keys
{
    cd $SSHDIR

    # create rsa key for SSHv1
    ssh-keygen -t rsa1

    # create rsa key for SSHv2
    ssh-keygen -t rsa

    # create dsa key for SSHv2
    ssh-keygen -t dsa
}

#
# function: push_keys(dest, port, tmpdir)
# descript: Copy the public keys to a machine whose trust you desire
# param: string hostname:/file destination
# param: int TCP Port#
# param: string Temporary Directory
#
function get_existing_keys
{
    scp -P $SSHPORT $SSHSERV:$SSHDIR_REMOTE/authorized_keys* $TMPDIR/
}

function merge_keys
{
    # copy the public identity and encryption keys to
    # a new 'temporary' file on the local system
    cat $SSHDIR/identity.pub >> $TMPDIR/authorized_keys
    cat $SSHDIR/id_dsa.pub $SSHDIR/id_rsa.pub >> $TMPDIR/authorized_keys2
}

function push_keys
{
    get_existing_keys

    merge_keys

    # set the proper permissions (644) for the authorized_keys file(s)
    chmod 644 $TMPDIR/authorized_keys*

    # copy the authorized_keys file(s) to the remote system
    scp -P $SSHPORT $TMPDIR/authorized_keys* $SSHSERV:$SSHDIR_REMOTE/

    # clean-up local directory
    rm $TMPDIR/authorized_keys*
}

#
# function: verify_deps
# descript: a simple function used to verify the dependencies
#
function verify_deps
{
    if [ ! -x $SSHDIR ]; then
        # mkdir -m 0700 $SSHDIR
        echo ""
        echo "Sorry, but it appears that you have not manually connected to a remote SSH Server yet."
        echo ""
        echo "We will now connect you to $SSHSERV..."
        echo "Please verify that the '~/.ssh' directory does exist on the remote machine. (ls -la | grep ssh;)"
        echo "If the directory does not exist on the remote machine, then you will need to create the directory, and try again. (mkdir -m 0700 ~/.ssh; logout;)"
        echo ""

        ssh $SSHSERV -p $SSHPORT
        exit 0;
    fi
}

function print_help
{
    echo "$0 - An RSA/DSA SSH Key Generator and Distribution Script"
    echo ""
    echo "Generate and Push New RSA/DSA Keys to a remote SSH Server:"
    echo "Usage: $0 [-g|--gen|-all]"
    echo ""
    echo "Push Existing RSA/DSA Keys to a remote SSH Server:"
    echo "Usage: $0 [-p|--push]"
    echo ""
}

case "$1" in
    '-p' | '--push')
        if [ $2 ]; then
            unset SSHSERV
            SSHSERV=$2
        fi
        if [ $3 ]; then
            unset SSHPORT
            SSHPORT=$3
        fi
        if [ $4 ]; then
            unset SSHDIR_REMOTE
            SSHDIR_REMOTE=$4
        fi
        push_keys
    ;;
    '-g' | '--gen' | '-all')
        # verify the dependencies
        verify_deps
        
        generate_keys 
        
        push_keys
        
        echo "Attempting to connect to: $SSHSERV:$SSHPORT..."
        
        sleep 5
        
        ssh $SSHSERV -p $SSHPORT
    ;;
    *)
        print_help
    ;;
esac 
```

---

### Post by onesojourner on 2009-12-02
ok maybe it is working:

```
peter@peter-Eeepc:~$ ssh -L 8080:desktop:80 peter@desktop
The authenticity of host 'desktop (192.168.1.146)' can't be established.
RSA key fingerprint is 9b:5b:63:23:7f:fe:10:f9:6b:09:b5:ce:ce:eb:a4:fc.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'desktop' (RSA) to the list of known hosts.
peter@desktop's password: 
Linux desktop 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

11 packages can be updated.
0 updates are security updates.

Last login: Sun Nov 29 09:08:33 2009 from peter-eeepc
peter@desktop:~$ 

```

I think I may be getting close now:
```
peter@peter-Eeepc:~$ rsync -avz --delete --rsh="ssh -p22 -i /home/peter/.ssh/id_dsa.pub" --exlude=*.flac user@192.168.1.146:/3storage/music /1storage/music
rsync: --exlude=*.flac: unknown option
rsync error: syntax or usage error (code 1) at main.c(1440) [client=3.0.6]
peter@peter-Eeepc:~$
```

---

### Post by onesojourner on 2009-12-03
I think I have made a little more progress tonight, but it's sill not working correctly.

```
peter@peter-Eeepc:~$ rsync -avz --delete --rsh="ssh -p22 -i .ssh/identity" --exclude=*.flac peter@192.168.1.146:/3storage/music /1storage/music
peter@192.168.1.146's password: 
receiving incremental file list
rsync: link_stat "/3storage/music" failed: No such file or directory (2)

sent 20 bytes  received 10 bytes  2.86 bytes/sec
total size is 0  speedup is 0.00
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1523) [receiver=3.0.6]
peter@peter-Eeepc:~$ 

```

---

### Post by sgosnell on 2009-12-03
It's saying it can't find the directory /3storage/music.  Linux directories and filenames are case sensitive, if you didn't know.  Does that exact directory exist?

---

### Post by onesojourner on 2009-12-03
wow... idiot move on my part. I will double check tonight.

---

### Post by onesojourner on 2009-12-04
yep I had the directory wrong. it is working now. I need some more help though. I would like it to sync up when ever I get on my home network automagically with out having to use a password. 

I have tried to go through this: [http://www.seanodonnell.com/code/?id=68](http://www.seanodonnell.com/code/?id=68)
 but I get an error. I will try it one more time and report back tomorrow.

---

