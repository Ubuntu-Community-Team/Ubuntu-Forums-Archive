---
title: "Sync Script"
date: 2010-07-18
forum: General Help
---

### Post by Forbees on 2010-07-18
wrote a script to sync my netbook music with my server music and everything was fine.

but if for some reason lets say i run it accidently and i'm not connected to my network, i just wiped my netbook music 

here's what i got so far:
```

Sudo mkdir /media/ServerMusic/
mount -t cifs -o user=Justin,password=****** //192.168.1.108/Public-3/Music/ /media/ServerMusic/
rsync -v -P --delete --min-size=500 -r -u /media/ServerMusic/ /home/forbees/Music/
umount /media/ServerMusic/
rm -r /media/ServerMusic/

```

i need to have the --delete option in rsync (say i sync it and realize i hate some music, when i delete it from the server i don't want it still on the netbook



i want an if statement in here somehow, but i'm not sure how to do it

something like, the first command in the script should be a ping test, if ping doesn't work end the script, if ping does work continue


ooorrrrr, if the server music gets mounted to the created directory continue, if the mount failed, or even in the mounted folder is empty stop the script


what can i do here to ensure i can keep the --delete and not have to worry about losing my music if the mount fails?

---

### Post by Zorgoth on 2010-07-18
After you execute mount, there will be a variable $?.  If this variable is zero the mount was successful, otherwise not.

I think.

---

### Post by Forbees on 2010-07-18
how would you write that in the script?

---

### Post by Zorgoth on 2010-07-18
Type "man bash" in the terminal for a general description of bash.


Here is basically what you need to do:

```

if [[ 0 == $? ]]
then
    proceed_as_normal
else
    error_message
fi

```

Note that the spaces in the "if" expression are essential.

---

### Post by fragos on 2010-07-18
I use Unison to sync folders between my laptop and desktop over WiFi using NFS. I never have any surprises.

---

### Post by Forbees on 2010-07-18
i've had problems with unison and security before (since you have to login to access the finals)

i'll try out that code once i'm done resyncing my netbook (reasons why i'm looking into this script . . i ran it when i wasn't connected, synced my music folder with an empty folder lol)

hope it works

---

### Post by Forbees on 2010-07-18
> **Zorgoth said:**
> Type "man bash" in the terminal for a general description of bash.


Here is basically what you need to do:

```

if [[ 0 == $? ]]
then
    proceed_as_normal
else
    error_message
fi

```

Note that the spaces in the "if" expression are essential.



whats the "fi" at the end for? is that a typo or needed lol

---

### Post by Zorgoth on 2010-07-18
This may be obvious, but remember to put the if precisely after the mount command.

---

### Post by Zorgoth on 2010-07-18
The fi is necessary.  It defines the end of the if block.  I would recommend reading man bash.

---

### Post by Forbees on 2010-07-18
k, just wanted to make sure, i only have a little programming knowlege

(basic, C++, java) back in highschool, so i wasn't sure if a script needed something to define the end or not (some basic level macro programing IF commands only work with one line of code, than assume the next line isn't a part of it)

---

### Post by lkjoel on 2010-07-18
> **Forbees said:**
> whats the "fi" at the end for? is that a typo or needed lol
You are not alone! I was thinking the same thing a while ago!
It just says that it is the end of the if statement.

---

### Post by Forbees on 2010-07-19
that variable isn't working . . . .

---

### Post by lkjoel on 2010-07-19
What variable isn't working?

---

### Post by Zorgoth on 2010-07-19
$? I believe he is referring to.  Is it really the variable that isn't working?  Try running the mount command in a terminal followed by "echo $?"

My suspicion is that you have a typo/error in the way your script is set up.  Post it please (exactly).

---

### Post by lkjoel on 2010-07-19
You can test the ? variable like this:
Test 1:
```
echo hello
echo $?
```
It should output 0

Test 2:
```
hffees
echo $?
```
It should output something like 127

Both of the tests should work.

---

### Post by Forbees on 2010-07-19
okay, the echo output did say $?=0 . . .

when i run the script it closes so fast i can't read the error, but i could have sworn i saw something to do with $? . . .

and awesome  . . . for some reason it didn't unmount before deleting the directory so i just lost 60gig of music :-/

so you can yell at me since i obviously did something wrong lol
```

sudo mkdir /media/ServerMusic/
sudo mount -t cifs -o user=Justin,password=****** //192.168.1.108/Public-3/Music/ /media/ServerMusic
if [[0=$?]]
then
rsync -v -P --delete --min-size=10000 ir iu /media/ServerMusic/ /home/forbees/Music
sudo umount /media/ServerMusic/
sudo rm -r /media/ServerMusic/
echo "sync successful"
else
sudo umount /media/ServerMusic/
sudo rm -r /media/ServerMusic/
echo "mount failed"
fi

```

---

### Post by Forbees on 2010-07-19
> 
and awesome . . . for some reason it didn't unmount before deleting the directory so i just lost 60gig of music :-/


the majority of it was still on my netbook thankfully . .  so now i just have to go through and find missing files(certain tracks from albums are still gones :-/ )

---

### Post by Zorgoth on 2010-07-19
You failed to include the spaces I mentioned in the if expression.

You have to say
```

if [[ $? == 0 ]]

```

rather than
```

if [[$?==0]]

```

Don't ask me why; I don't get it either.

OH - YOU ALSO NEED 2 EQUALS SIGNS.

This is ordinary in programming.  = is assignment, == is comparison.

I hope your music is OK; in the future when writing important scripts be sure to test every component before using them in practice.

---

### Post by Zorgoth on 2010-07-19
Also, I would recommend that you make /media/ServerMusic an empty directory when not mounted, and then rather than that dangerous "rm -r" you could use "rmdir", which will fail if there are files in the directory.

---

### Post by lkjoel on 2010-07-19
> **Forbees said:**
> okay, the echo output did say $?=0 . . .

when i run the script it closes so fast i can't read the error, but i could have sworn i saw something to do with $? . . .

and awesome  . . . for some reason it didn't unmount before deleting the directory so i just lost 60gig of music :-/

so you can yell at me since i obviously did something wrong lol
```

sudo mkdir /media/ServerMusic/
sudo mount -t cifs -o user=Justin,password=****** //192.168.1.108/Public-3/Music/ /media/ServerMusic
if [[0=$?]]
then
rsync -v -P --delete --min-size=10000 ir iu /media/ServerMusic/ /home/forbees/Music
sudo umount /media/ServerMusic/
sudo rm -r /media/ServerMusic/
echo "sync successful"
else
sudo umount /media/ServerMusic/
sudo rm -r /media/ServerMusic/
echo "mount failed"
fi

```

 ```

sudo mkdir /media/ServerMusic/
sudo mount -t cifs -o user=Justin,password=****** //192.168.1.108/Public-3/Music/ /media/ServerMusic
if [[$? == 0]]
then
rsync -v -P --delete --min-size=10000 ir iu /media/ServerMusic/ /home/forbees/Music
sudo umount /media/ServerMusic/
sudo rm -r /media/ServerMusic/
echo "sync successful"
else
sudo umount /media/ServerMusic/
sudo rm -r /media/ServerMusic/
echo "mount failed"
fi

```

---

### Post by Forbees on 2010-07-19
and that is the reason i stopped programming lol..

i did have two "="'s, i just forgot when typing here on the forum, can't copy past since i'm not on my netbook

but i did have the backwards variables and forgot the spacing

i blame you for the backwards variables :-p in your example you had them that way lol

idk why, but i don't like the idea of empty folders laying around . .  so i think i'll switch it to rmdir

i also changed the permissions on my server to read only to ensure i can't mess up like that again lol

---

### Post by Zorgoth on 2010-07-20
I don't think it matters which way the variables go; I'm pretty sure I had them that way when I was testing.

---

### Post by Forbees on 2010-07-20
hmm . . . now it's saying MusicSync.sh is not found when i run it . . . how can it not find the script i just opened? lol

---

### Post by Zorgoth on 2010-07-20
Perhaps the permissions are not set to executable?

Do "chmod +x" on it.

You could also try running it with the command "bash"

---

### Post by Forbees on 2010-07-20
i did chmod it, but not since i last edited it, so i guess that could make sense to have to chomd it again

k, now the script runs and syncs, but when i error tested it by running dicconected to the network it's crawling and snail speed to realize that it won't work

also, it seems as if it didn't even go through the "else" portion of the code.

i just said can't mount and exited terminal, didn't run any of the commands i told it to if the mount failed

---

### Post by lkjoel on 2010-07-20
I just want to make sure... you do know what the ? variable is right?

---

### Post by Forbees on 2010-07-20
erm, if i did i wouldn't be on here lol

i stopped programming almost three years ago, and that was C++/Java.  i've only written 3 scripts in linux before and they were all simple things like disable copmiz and run a game etc

---

### Post by lkjoel on 2010-07-20
The ? variable says the status.
So if there was no errors, it would give a status of 0.
If there was one, it would not give a status of 0.
Usually it would be 127 if there was an error.
But some programmers tell it to have a status of X.
To tell the status, you have to type:
```
exit X
```
where X is the status.
A good example of that is on: [http://linuxessentials.googlecode.com/files/DEtools.tar.gz](http://linuxessentials.googlecode.com/files/DEtools.tar.gz)
If you check thee source code of showde, you will find that it will exit with a status of 1, 2 or 3.
Each depending on the DE.

---

### Post by Forbees on 2010-07-20
with that being said the script should run flawlessly. . . .

---

### Post by lkjoel on 2010-07-20
```
sudo mkdir /media/ServerMusic/
sudo mount -t cifs -o user=Justin,password=****** //192.168.1.108/Public-3/Music/ /media/ServerMusic
if (($? == 0))
then
rsync -v -P --delete --min-size=10000 ir iu /media/ServerMusic/ /home/forbees/Music
sudo umount /media/ServerMusic/
sudo rm -r /media/ServerMusic/
echo "sync successful"
else
sudo umount /media/ServerMusic/
sudo rm -r /media/ServerMusic/
echo "mount failed"
fi
```

---

### Post by Forbees on 2010-07-20
acidental double post

---

### Post by Forbees on 2010-07-20
> **lkjoel said:**
> ```
sudo mkdir /media/ServerMusic/
sudo mount -t cifs -o user=Justin,password=****** //192.168.1.108/Public-3/Music/ /media/ServerMusic
if (($? == 0))
then
rsync -v -P --delete --min-size=10000 ir iu /media/ServerMusic/ /home/forbees/Music
sudo umount /media/ServerMusic/
sudo rm -r /media/ServerMusic/
echo "sync successful"
else
sudo umount /media/ServerMusic/
sudo rm -r /media/ServerMusic/
echo "mount failed"
fi
```



that is the code i'm using, only i changed rm -r to rmdir . .  and there are a few spelling errors in there (i didn't copy pasta)

```
sudo mkdir /media/ServerMusic/
sudo mount -t cifs -o user=Justin,password=****** //192.168.1.108/Public-3/Music/ /media/ServerMusic
if (($? == 0))
then
rsync -v -P --delete --min-size=10000 -r -u /media/ServerMusic/ /home/forbees/Music/
sudo umount /media/ServerMusic/
sudo rmdir /media/ServerMusic/
echo "Sync Successful"
else
sudo umount /media/ServerMusic/
sudo rmdir /media/ServerMusic/
echo "Mount Failed"
fi
```

during the error test, i ran this while not connected to the network, so the mount failed, which should have made $? =/ 0, which than should have ran the "else" code, but it didn't. terminal closed itself without the output of "Mount Failed" and Dir ServerMusic still existed

---

### Post by lkjoel on 2010-07-20
```

sudo mkdir /media/ServerMusic/
sudo mount -t cifs -o user=Justin,password=****** //192.168.1.108/Public-3/Music/ /media/ServerMusic
if (($? == 0))
then
rsync -v -P --delete --min-size=10000 -r -u /media/ServerMusic/ /home/forbees/Music/
sudo umount /media/ServerMusic/
sudo rm -R /media/ServerMusic/
echo "Sync Successful"
else
sudo umount /media/ServerMusic/
sudo rm -R /media/ServerMusic/
echo "Mount Failed"
fi
```

---

### Post by Zorgoth on 2010-07-20
OOPS!!!

Just looked at my post, formed a suspicion, rechecked man bash, and you should not be using parentheses but square brackets,

So

```

if [[ $? == 0 ]]

NOT

If (( $? == 0 ))

```

Sorry.  Typo...

---

### Post by Forbees on 2010-07-21
lkjoel's code is using ((  )). . . . 

i was hoping that'd be the problem but it wasn't

with either [[ ]] or (( )) same thing

works fine when connected, but will not run the ELSE commands when not connected

what it does instead is blank screen for two minutes than:
mount error: mount point /media/ServerMusic/ does not exist
and it just stays like that . .

---

### Post by lkjoel on 2010-07-21
Two things:
First, is it possible to remove all the sudo's, then just run "sudo yourscript"?

Second, while not connected to the internet, run the mount command, then run:
```
echo $?
```
If it outputs 0, you have a problem.

---

### Post by Forbees on 2010-07-21
i suppose i could do that, but than i'd either have to run it in termninal, or make a new script to open the old script with sudo previlages

ran mount command while not conected, $? = 32

. . . . . . . . i don't see why it's not running the else . .. .

---

### Post by Zorgoth on 2010-07-21
What happens if you execute ONLY the mount command?

Oh, and you are trying to umount /media/ServerMusic when nothing is mounted there in the else block I believe, no?

---

### Post by Zorgoth on 2010-07-21
By the way, I do not know if this is a problem, but you may not want to execute it with password=******.  I believe that if you do that you will find that if you run

cat /etc/mtab | grep password

your password will be displayed.  Anyone could do this without root permissions.

This may not occur; it might be designed so this doesn't happen.  But be careful whenever passing your password as an argument to a function that it is not displayed in the output of "ps -e" or "cat <some_relevant_system_file>"

And I *SERIOUSLY* recommend using rmdir, not rm -r, on /media/ServerMusic at the end.  If you do not, you are doing to wipe out your server music if there are any errors.

---

### Post by tgm4883 on 2010-07-21
Out of curiosity, are you sure it isn't running the else block? Maybe it is just exiting the terminal so fast you can't tell?

---

### Post by Forbees on 2010-07-21
yeah . .  now thinking about it that is a pointless line lol

hmm . . . now i think it might be working, but it opens and closes too fast so i can't really troubleshoot it.

so i added a "press anykey to close" command . . .

and now it's not syncing which is good . .  but it's not running the else . .  it's trying but not running it

fails to rmdir

---

### Post by Zorgoth on 2010-07-21
You may want to ensure that the /media/ServerMusic on your actual hard drive is empty; your earlier problems probably caused files to be put there.

---

### Post by tgm4883 on 2010-07-21
Ok, i've been playing around with this for a bit and this code works for detecting my usb drive being attached. You should just need to edit /media/PENDRIVE to /media/ServerMusic

It should still work because we aren't checking if the directory exists, but rather that it is a mount point.

Obviously you would need to add in your mount and remove commands, but I would just test this first
```
grep -q /media/PENDRIVE /etc/mtab
if [ $? == 0 ]; then
  echo "sync successful"
else
  echo "mount failed"
fi
```

---

### Post by Forbees on 2010-07-22
i have to use the password to access the server shares . .  i did change it to rmdir

after more troubleshooting, it is running the else section, but it two commands are running

umount and rmdir

those two in the code don't do anything and come with an error "device is busy"

---

