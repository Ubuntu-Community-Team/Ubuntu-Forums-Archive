---
title: "Using rsync to share home directories. (plus some other things)"
date: 2010-08-27
forum: General Help
---

### Post by coteyr on 2010-08-27
So I am not sure if this is in the right forum but I intend to write an article and setup a system, where I can keep all my computers in sync. 

**The goals (MoSCoW form)**
Must Haves
[LIST]
[*]Sync $HOME
[*]Sync Across the network
[*]Run in the background
[*]Not fail if one of the machines or syncs fail (i.e. not connected to the right network 
[/LIST]
Should Haves
[LIST]
[*]Should sync packages
[*]Should Provide some kind of report on latest sync attempts
[*]Should be able to be run manually
[*]List packages that are not installable on a machine (i.e. different arch or not installed from the repos
[/LIST]
Could Haves
[LIST]
[*]Might sync package sources
[*]deb package for instillation
[/LIST]
Won't Haves
[LIST]
[*]GUI for configuration (should be so simple it doesn't need one)
[/LIST]

**The story/situation**
The whole point of this is that I have 4 machines that I use on a regular basis, and I have never found a piece of software that can do this. I have found bit and pieces here and there but they are always a bare to get installed. In addition this really should amount to much more then a bunch of bash scripts and cron jobs, so it should be pretty simple to do. 

What I am looking for is a simple way to keep all *my* settings the same between all these computers. To have all the documents automatically propagate between one machine and the other. I want to do this not only for documents but settings and applications as well. 

rsync seems to be the way to go for most of the sync process. The only real problem is that it might have merge issues (sorry not sure of the correct jargon here). 

**Why this thread?**
Easy, I want community input and I hope this is something that can be shared with the community. I am sure I will run into problems and I am sure there will be other solutions to those problems. In addition, as stated, I would like this to be something that others can use. I think almost everyone would like some form of this, even if just for a few directories and not the entire home directory.

---

### Post by coteyr on 2010-08-27
First thing is fist lets get rsync setup on the home directory and lets get it running over ssh. 

```

sudo apt-get install rsync

```

Lets also setup two test directories on the same machine (for now) to play with.

```

cd
mkdir test-home1
mkdir test-home2

```

Then lets put a file in each diretory
```

touch test-home1/home1.txt
touch test-home2/home2.txt

```

Now according to the rsync man page what we should be running is
```

rsync -r -u -l --safe-links -p -E -z --progress -i --log-file=/tmp/sync.log $HOME/test-home1/ $HOME/test-home2/

```

What this does not cover is deletes? Lets test it and find out. After testing this gives us a one way sync between home one and home 2. Lets find a way to do a two way sync. 
```

rsync -r -u -l --safe-links -p -E -z --progress -i --log-file=/tmp/sync.log  $HOME/test-home2/ $HOME/test-home1/

```

That gives us a nice two way sync but there are no deletes being synced. We can test this by 
```

touch $HOME/test-home1/delete-me.txt
rsync -r -u -l --safe-links -p -E -z --progress -i --log-file=/tmp/sync.log $HOME/test-home1/ $HOME/test-home2/
rsync -r -u -l --safe-links -p -E -z --progress -i --log-file=/tmp/sync.log  $HOME/test-home2/ $HOME/test-home1/
rm $HOME/test-home2/delete-me.txt
rsync -r -u -l --safe-links -p -E -z --progress -i --log-file=/tmp/sync.log $HOME/test-home1/ $HOME/test-home2/
rsync -r -u -l --safe-links -p -E -z --progress -i --log-file=/tmp/sync.log  $HOME/test-home2/ $HOME/test-home1/

```

This is where it starts to get iffy on us. The problem is how do we know who's file to delete. As you can see in the test above we synced the directories and deleted a file. the synced again and because of of the directories had the "deleted" file it put it back in both directories. I don't know about you but I do not want un-deletable files running around.  Ok so were going to have to scratch rsync. There is however a program out called unison that might do what we need. 

```

sudo apt-get install unison

```  

This is where will will pick up in the next post (momentarily). Just too keep things clean.

---

### Post by coteyr on 2010-08-27
Rsync did not work for us. It could not handle the deletes. That takes us to unison. Unison is a good app, but I have never really liked the gui. Thankfully it's not needed. Now that we have it installed lets try it.

```

unison $HOME/test-home1 $HOME/test-home2

```

The command makes us answer some questions but other then that it seems to be ok. We can override the asking of questions by passing the -batch argument.  Now lets test our delete again.

```

rm $HOME/test-home1/delete-me.txt
unison -batch  $HOME/test-home1 $HOME/test-home2

```

Now we are getting somewhere. Lets test a file conflict. 

```

echo "I am in home 1" > test-home1/conflict.txt
echo "I am in home 2" > test-home2/conflict.txt
unison -batch  $HOME/test-home1 $HOME/test-home2

```

well here we have another problem. The file was not propagated because it was conflicting. This is not a bad default behavior, but we want everything to be in sync. However this is again a dicey situation. We can not have one file overwrite another because of a time stamp. You wouldn't want to loose all your work on one machine because you also happened to save a file on a second machine with the same name. You also probably don't want one file overwriting the same file on another machine because we said one machine ALWAYS has the latest copy, but in real life those are our only options. Because I work from a machine 90% of the time. I will choose that machine to be the preferred source of the "correct" file. Knowing that I may loose data on one of the other machines. 

```

unison -batch  $HOME/test-home1 $HOME/test-home2 -prefer $HOME/test-home1 # you could also use -prefer newer or -prefer older

```

Conflicts are addressed deleting is addressed but we are tying commands by hand lets create a script.

In $HOME/coteyr_sync
```

# the first root directory
ROOT1="$HOME/test-home1"
# the second root directory
ROOT2="$HOME/test-home2"
#which root to prefer you can also use "newer" and "older" without the quotes
PREFER="$ROOT1"

unison -batch $ROOT1 $ROOT2   -prefer $PREFER

```

This give us a few variables to play with and leaves us not having to type that entire command again. Do not forget to:

```

chomd +x $HOME/coteyr_sync

```

---

### Post by coteyr on 2010-08-27
We have unison working with two directories on a single machine but now we need it to work with two directories on different machines. Unison allows us to do this via ssh or the unison daemon. For security reasons we are going to use ssh. Unison requires you to have ssh and unison installed by default on the remote machine. Son on a second machine.
```

 sudo apt-get install unison openssh-server

```

Now we want this to run in the background silently so lets set up some ssh keys. The local machine will be the main machine that runs the unison commands. The remote machine will the one accepting the ssh connection. We need to establish a connection from the local machine to the remote machine, and we don't want to mess with passwords so we will use keys. 

on the local machine
```

ssh-keygen #you do not need this if you already have a key
ssh-copy-id user@remote_machine

```

Also it's important to note that because were doing this over the network we are going to want to have some static way of referencing all the machines. Some routers for home usage have built in DNS servers that will help with that others do not. You can almost always set static IP addresses. Which ever method you choose you are going to want to make sure that it doesn't change to frequently. You don't want to have to be editing the script/config files every few days to keep the sync working. 

Lets create some new testing directories and remove the old ones. 
On local
```

rm $HOME/test-home1 -rf
rm $HOME/test-home2 -rf
mkdir $HOME/test-local
touch $HOME/test-local/from_local.txt

```

on remote
```

mkdir $HOME/test-remote
touch $HOME/test-local/from_remote.txt

```

Now lets edit our script and change #HOME/coteyr_sync
```

ROOT1="$HOME/test-local"
ROOT2="ssh://remote/$HOME/test-remote" #do not forget to change this to the correct host

```

and run the script
```

$HOME/coteyr_sync

```

As you can see we are now working with two machines. And syncing a sub directory of the home directory. You are now going to want to move to syncing the home directory, but this is where it gets more entertaining. First and foremost **MAKE A BACKUP** of both home directories. We very well could mess up quite a few things. 

Next lets change the script again.
```

# the first root directory
ROOT1="$HOME/"
# the second root directory
ROOT2="ssh://remote/$HOME/"
#which root to prefer you can also use "newer" and "older" without the quotes
PREFER="$ROOT1"

unison -batch $ROOT1 $ROOT2 -prefer $PREFER -ignore "Path .ssh/" -ignore "Path .unison/" -ignore "Name *~" -ignore "Name *.bak"

```

The new ignore options ignore backup files and anything in the .ssh directory and the .unison directory. 

Go ahead and run the coteyr_sync script and lets watch what happens. 

(Updates after the script runs)

---

### Post by renkinjutsu on 2010-08-27
I say the best way to do this would be to PXE boot all of your machines to mount the same "/" and "/home" through NFS.. that way, all of your settings, and documents and applications will be consistent across all your computers all the time

I have never set up PXE before though =X

---

### Post by coteyr on 2010-08-27
The problem I have with that is it fails one of the Must Haves. If your network is down (or you move your machine to another network) then your screwed.

Syncing home directories is like the holy grail of network computing. Windows have Roaming profiles but man is that a mess. I know that in the end this method should work because I have copied me home directory from one machine to another with out a problem. Automating that should work fine. But it is a tad bit complex. The extra Should haves are nice. Like package syncs but we will have to see when the time comes that may be more trouble then it's worth.

> **renkinjutsu said:**
> I say the best way to do this would be to PXE boot all of your machines to mount the same "/" and "/home" through NFS.. that way, all of your settings, and documents and applications will be consistent across all your computers all the time

I have never set up PXE before though =X

---

### Post by renkinjutsu on 2010-08-27
But the problem with rsync is that when you don't use the --delete option, and you're going to be syncing both ways, it's going to cause problems (cluttering your directories with files you deleted)

and when you DO use the --delete option, it'll cause even more serious problems (deleting newly created files on your target system)

---

### Post by coteyr on 2010-08-27
Hence why I moved to testing unison instead of rsync. It "seems" to handle the deletes better. If you know a better way then unison then I will test that. I am not all that fond of unison but it seems to work. 
 

> **renkinjutsu said:**
> But the problem with rsync is that when you don't use the --delete option, and you're going to be syncing both ways, it's going to cause problems (cluttering your directories with files you deleted)

and when you DO use the --delete option, it'll cause even more serious problems (deleting newly created files on your target system)

---

### Post by coteyr on 2010-08-27
Update**  Unison is to damn slow over ssh to be any use. So we are going to have to modify the script again. This time lets try using the unison socket server. Not sure it will be much faster but we want to avoid running something like NFS or smb and sharing the entire $HOME. In addition lets also start the remote unison demon and stop it from the local machine, this will make sure the daemon is only running when we need it to. 

The new $HOME/coteyr_sync script
```

# the first root directory
ROOT1="$HOME/"
# the second root directory
ROOT2="socket://remote:26839/$HOME"
#which root to prefer you can also use "newer" and "older" without the quotes
PREFER="$ROOT1"

ssh remote "unison -socket 26839" &
REMOTE_UNISON=$!
unison -batch $ROOT1 $ROOT2 -prefer $PREFER -ignore "Path .ssh/" -ignore "Path .unison/" -ignore "Name *~" -ignore "Name *.bak"
kill $REMOTE_UNISON

```

The new lines of code start the unison socket demon on the remote machine, then later kill the ssh session that has the command open. The rest is pretty self explanatory. 

I am not sure why ssh was moving so horridly slow, but it was. We will have to wait and see how well this works out.

---

### Post by coteyr on 2010-08-28
Well Seems the socket server isn't any faster so back to the ssh method. Also the unison program does not seem exactly stable when transferring large files. So to help it out were going to limit it down a bit and just sync one directory at a time. This slows down the process a bit because it has to keep connecting to the server, but it creates a more stable situation. 

```

# the first root directory
ROOT1="$HOME/"
# the second root directory
ROOT2="ssh://upstairs/$HOME/"
#which root to prefer you can also use "newer" and "older" without the quotes
PREFER="$ROOT1"

cd "$ROOT1"
shopt -s dotglob
for i in *; do
  if [ -d "$i" ]; then
    echo "****Syncing $i"
    #unison  -batch $ROOT1 $ROOT2 -prefer $PREFER -path "$i/" -ignore "Path .ssh" -ignore "Path .unison" -ignore "Name *~" -ignore "Name *.bak" -ignore "Path .VirtualBox" -ignore "Path .cache/" -rshargs -C -maxthreads 1
  fi
done
unison  -batch $ROOT1 $ROOT2 -prefer $PREFER -ignore "Path .ssh" -ignore "Path .unison" -ignore "Name *~" -ignore "Name *.bak" -ignore "Path .VirtualBox" -ignore "Path .cache/" -rshargs -C -maxthreads 1

```

The reason for the new ignores is because I had huge files there. Running unison per directory seems to provide more stable results.  Running unison one more time on the root, brings over directories that you might not have on your local machine that you do have on your remote machine. It also sync the top level files in $HOME.

**BE WARNED!**
The first time you run this sync it's going to take FOREVER. It would be much better to restore that back you made earlier (you did do that right) to both your local and remote machine and then sync so that you have fewer files to transfer. Also don't go deleting things on either host until after your first sync. Because unison has no idea about what is there it will not know not to copy things back. Wait for the first sync to complete then you should be able to continue like normal.

We will generic-ize the script a bit a little latter. 2 of the must haves are done, the other two will have to wait till we get more machines. Lets focus on syncing installed packages.

First we only want to sync manually installed packages. We don't want to sync the auto installed stuff. We want to see that "Package blah blah is no longer required" message. So lets start by getting a list of manually installed packages. the best way I have found to do this is
```

aptitude search '?installed ?not(?automatic)'

```

So lets create a file called $HOME/coteyr_pakages_sync (we will combine these later into one nice big file but for now lets keep them separate so we can keep testing)
```

#!/bin/bash
REMOTE='remote'
ssh $REMOTE "DEBIAN_FRONTEND=noninteractive sudo apt-get update"
for package in `aptitude search '?installed ?not(?automatic)' -F '%p'`; do
  ssh $REMOTE "DEBIAN_FRONTEND=noninteractive sudo apt-get -y install $package"
done

```

Again remember to change the REMOTE address to your "other" machine. Notice the DEBIAN_FRONTEND environment variable. This is telling apt-get (more correctly debconf) That you have no way to see any of the questions and to just guess. This will cause you problems with packages that require configuration as you have given them none. However, you can always dpkg-reconfigure so this seems like a fair trade. Most of the time you will get a bunch of errors about packages already being installed, but the first time, expect the sync to take a long time again. 

**[SIZE="7"]HUGE WARNING TIME[/SIZE]**
This runs sudo so it effectively runs as root on the remote machine. You need to know and understand this before you try this command. If you go messing up your packages then you could really be in a pickle. Try this one way, on a testing machine first. If your happy with the results then go ahead and use it. It *should* be harmless, and it *should* just work. But you could also really mess things up.

For saftey's sake we will not be synchronizing package deletes. Better to have a few extra programs around then every synced machine just not working.

Lets give this a try

---

### Post by coteyr on 2010-08-28
Ok so ssh sudoing is not the bast thing, so lets revise that a bit. Also running apt-get install 900 times when you already have those packages is a bit of a pain as well.

Lets start with a new $HOME/coteyr_sync_packages
```

#!/bin/bash
REMOTE='upstairs'
aptitude search '?installed ?not(?automatic)' -F '%p' > local.packages
ssh $REMOTE "aptitude search '?installed ?not(?automatic)' -F '%p'" > remote.packages
rm inst.packages
for lp in `cat local.packages`; do
  noproc="false"
  for rp in `cat remote.packages`; do
    if [ "$lp" == "$rp" ]; then
      noproc="true"
    fi
  done
  if [ "$noproc" != "true" ]; then
    echo "$lp" >> inst.packages
  fi
done
scp inst.packages $REMOTE:/tmp/install.packages
rm inst.packages
for lp in `cat remote.packages`; do
  noproc="false"
  for rp in `cat local.packages`; do
    if [ "$lp" == "$rp" ]; then
      noproc="true"
    fi
  done
  if [ "$noproc" != "true" ]; then
    echo "$lp" >> inst.packages
  fi
done
mv inst.packages /tmp/install.packages

```

Now that puts the package that need to be installed on the remote machine. We can let the remote machine decide what to do with them. This also gives us the packages to install on our local machine to make it match the remote machine. I would like to find a grep statement or something that would for to rid us of those ugly for loops, but alas, this does work.  The actually installing of the packages we will like for later. This now just gets us the list. 

In the future we will need to secure this list a lot better. Our intent is to list in package in /tmp/install.packages, but thats not very smart as anyone can write to it. We will need to make the package installer run as root, and make the install.packages file exist in a more secure location.

When we start combining this into a actual script instead of just tests and chunks of code we will want to be able to turn off some features, and turn others on. Not to mention full configuration of paths and such.

---

### Post by coteyr on 2010-08-28
OK let continue with the package installer. 

So we have a list of packages that need to be installed on a machine. Were going to read though the list and install the packages one at a time. But we also need to ignore some packages. For example we want to not install the Nvidia packages on a machine with an ATI card. Also some wireless drivers and some other kernel things. Plus you may just have some packages you don't want shared. Lets go ahead and create a file with a list of packages to be ignored. 

Create the file $HOME/.coteyr_sync/ignore.packages
```

bcmwl-kernel-source
fglrx-modaliases

```

You will almost certainly want this list to be larger. Also note that we created a directory to hold the file. We don't want are home directory getting all cluttered and we also want these to be specific to a machine (and not synced).

Now lets go ahead and write the package installer.

so create $HOME/coteyr_sync_package_installer
```

#!/bin/bash
apt-get update
for package in `cat /tmp/install.packages`; do
  noproc="false"
  for ignore in `cat $HOME/.coteyr_sync/ignore.packages`; do
    if [ "$package" == "$ignore" ]; then
      noproc="true"
    fi
  done
  if [ "$noproc" != "true" ]; then
    DEBIAN_FRONTEND=noninteractive sudo apt-get -y install $package
  fi
done

```

Notice this time we did not call sudo in our script. So the script has to be run with sudo (or root permissions). Go ahead and run it and it will install all the packages that are on your remote machine to your local machine. 

Up till this point we have been having One system act at the "starter" of the sync. But when we want to sync more then one computer it will be a good idea to be able to start the connection from either side. Unfortunately, the scripts and what not are now synced over so making a change on the remote machine modifies settings on the local machine. This is what we want over all but we need different values for our variables on each machine. To accomplish that we will need to edit our scripts again. This is a good time to make them a bit more generic and to combine them. It's also a good time to refactor them a bit and DRY them up a bit.

---

