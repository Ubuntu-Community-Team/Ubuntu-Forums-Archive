---
title: "Help Building a Startup Shell Script"
date: 2010-04-18
forum: General Help
---

### Post by ngrieb on 2010-04-18
I'm looking to make a launching script which launches a program in one of the current directories that the user has open, the problem is I have no idea how to get info about all of the terminals open. 

I simply want to check which directories the user has open and do a pwd on the terminals, and then use that to cd into the dir before launching. I might be able to use a combo of who,tty, top, and pwd...but I don't know where to go. If anyone anyone has a better understanding of shell scripting I would really appreciate it. 

Thanks in advance.

---

### Post by quadproc on 2010-04-18
> **ngrieb said:**
> I'm looking to make a launching script which launches a program in one of the current directories that the user has open, the problem is I have no idea how to get info about all of the terminals open. ...

Are you wanting to run something in the user's terminal?
Do you want your code to execute from that user's terminal environment?
Do you need to respect the user's "PATH" variables?
Do you want this function to run even if the user has done something like "cd /"?

Assuming that it is possible to do what you want, the supervisory daemon will have to run with root privilege.  This can pose a security problem unless you build a lot of security into the daemon.

quadproc

---

### Post by ngrieb on 2010-04-18
Well, the user would be the one executing the script, so I don't believe that any root permission needed there. 

I simply want to look for the terminals I have open under my user name (a list, like the second row of the who command), and open the program within the directory accessed by one of these terminals (ie do a pwd in the open tty's) so that I don't have to search through the file browser to find the active terminals. 

Essentially I just want the shell script to return a list of directories that are actively opened in one of a number of terminals...from there I can loop them in zenity or something and get the user to specify which dir is the correct one.

---

### Post by quadproc on 2010-04-18
> **ngrieb said:**
> Well, the user would be the one executing the script, so I don't believe that any root permission needed there. How will you get the user to execute the script every time a new terminal is activated?> 
I simply want to look for the terminals I have open under my user name (a list, like the second row of the who command), and open the program within the directory accessed by one of these terminals (ie do a pwd in the open tty's)The pwd command returns the name of the user's working directory; this is the place where the system will operate on the user's data files unless the user specifies a fully qualified path.  It is not related to where the program files are located; you can find those in the $PATH variable.>  so that I don't have to search through the file browser to find the active terminals. I do not understand what you mean by "open the program".  Taken literally, that statement means to open a code file for reading and I do not think that that is what you intend.> 

Essentially I just want the shell script to return a list of directories that are actively opened in one of a number of terminals...from there I can loop them in zenity or something and get the user to specify which dir is the correct one.How do you want to get the information transmitted to you?  Placed into a file that you can access?  Placed into a pipe which connects to a daemon of your own creation?  Something else?

quadproc

---

### Post by ngrieb on 2010-04-19
Sorry. I don't know why there is so much confusion here, but let me try again:

I want the user to simply click an icon which will execute the shell script.

The shell script should search for the directory(ies) that are currently open, 
and execute the program from within the directory.

I want this to happen because when the program is executed in a certain directory 
it then establishes that the directory is the present working directory, and the user 
then does not need to browse all over the file system for the correct working directory.

(i.e. if I open the program from the terminal while in /home/username and attempt to 
open a file it first opens the dir /home/uername)

---

### Post by quadproc on 2010-04-19
> **ngrieb said:**
> Sorry. I don't know why there is so much confusion here, but let me try again:

I want the user to simply click an icon which will execute the shell script.OK, I will assume that you can implement the icon.  Be sure that the script permissions include execute for all your users.
> 
The shell script should search for the directory(ies) that are currently open, 
and execute the program from within the directory.There isn't any searching required; the working directory is already known to the shell.
> 
I want this to happen because when the program is executed in a certain directory 
it then establishes that the directory is the present working directory, and the user 
then does not need to browse all over the file system for the correct working directory.I am not really following you here but I will proceed with the idea of logging the user's working directory when the user selects and runs the script.> 
(i.e. if I open the program from the terminal while in /home/username and attempt to 
open a file it first opens the dir /home/uername)My assumptions may be wrong and this script may not do what you want, but at least it may give you some ideas that you might incorporate into your solution.

Assumption 1: the user has a bin directory in his home directory.  The program that you wish the user to execute lives in that directory, and has appropriate ownership and permissions.  I named that program "pgm_to_execute" but you can change this to whatever works.

Assumption 2: You will have a log file which lives in /usr/share/managed_data/pwd_collector.  This file needs to have read and write permissions for the system administrator (probably you), and it needs to have at least write permissions for everybody.  Of course, you can change the name and location of this file to suit your installation.  You will need to create this file before running the script.  You will also need to clean it out from time to time.  You will need root privileges to set some of its characteristics.

Assumption 3: The log file will include the user name, the user's working directory, and the date and time.

Assumption 4: You would like the user to know that the script has finished when it is done.

The following script is run by inputting on a command line```
bash <scriptname>
```The script itself is not written the way that a script would normally be written.  This vserion uses unnecessary variables; it is written that way to make it more self documenting.  It would be easy to shrink it.
```
#!/bin/bash
scriptname="Working directory collector"
pgm_to_execute="bin/pgm_to_execute"
collected_directory_names="/usr/share/managed_data/pwd_collector"

fromwho=`who`
frompwd=`pwd`
firstwho=`(echo $fromwho | cut -d' ' -f1)`
todaysdate=`date --rfc-3339=seconds`
echo $firstwho" using "$frompwd" at "$todaysdate >> $collected_directory_names
. $pgm_to_execute
echo $scriptname" has finished"

```
Also please note that the script does not do any error checking.  I omitted this for simplicity.

quadproc

---

### Post by ngrieb on 2010-04-20
Thanks, but it seems very round about for a simple task. Is there not a way to just access other terminals through /dev/pts/X somehow, if it was initialized by the same user? I tried this:
/dev/pts/2 pwd
, but I get permission errors. I mean it seems like if this would work, it would be all I need. Is there some way to access one terminal from another in such a way?

---

### Post by quadproc on 2010-04-20
> **ngrieb said:**
> ... Is there not a way to just access other terminals through /dev/pts/X somehow, if it was initialized by the same user?
Devices are a rather sacred thing to the operating system.  In general, a device is associated with a driver and the driver is associated with the OS.  It has to be this way to allow the system to function properly.

Consider what happens when a device generates an interrupt (for example, when a user types a character on the keyboard): the system has to figure out where the interrupt came from, what the system should do about it (in this case, collect the character and place it into some place in the keyboard's buffer, check to see if another process (such as the program which has the keyboard assigned to its input) needs to be awakened to process the new character, see if the new character requires immediate action (such as control-C causing a signal to be sent to the appropriate task).

All of that has to occur in an orderly and predictable fashion, otherwise the cause of the interrupt can be lost and the system won't know what to do about it.

So, users generally cannot directly access devices.  A knowledgeable user can circumvent these protections but doing so is risky; total system failure is a possibility.

You might want to learn a little about _message control systems_.  These are portions of a computer's operating system which manage the transfer of messages from various sources to various destinations.  The message can be anything; for example, it can be binary values relating to temperatures of the CPU, it can be the contents of a pipe file, it can be a line of text to be printed, it can be a single character.  The MCS is also usually tasked with enforcing some kind of security on the system, for example it will probably manage the login process.

A closely related subject is _interprocess communication_ (IPC).  IPC exists where one process (task) wants to send or to receive something to or from another process.  In Linux this is often done with pipe files.  For example, if I execute```
 cat somefile | head
``` then both the cat and the head processes will be running and the two of them will be connected to each other with a pipe.  The shell sets up the pipe file as a result of the "|" character.  Several programs can be piped to each other: ```
cat somefile | tr '\t' ' ' | more 
```will substitute spaces for tabs in somefile and will display the result on the screen with paging.

One other loosely related thing is the _wall_ command.  It causes a message to be sent to all logged in terminals that have not denied messages (or all of them if the super user executes wall).  This is commonly found in shutdown scripts to warn users of the impending shutdown.

I am not sure that any of this will provide you with a simple solution to your problem, but at least the example script shows that a solution is possible.

quadproc

---

