---
title: "Would this script work?"
date: 2006-06-13
forum: General Help
---

### Post by Lunar_Lamp on 2006-06-13
I am almost certain that the answer is "no".  However, I would like some pointers, as I have never written any kind of script before.

What I want to do is trigger the script and have it update my sources, then perform an upgrade.  However, if I get a warning that my source list has duplicate entries, I want it to ask me what to do.

If someone could point me in the way of what I will need to change in here, I'd be much appreciative.

```
#!/bin/sh

UPDATE_OUTPUT=$(sudo apt-get update)
	
	if [ '$UPDATE_OUTPUT' = "*W: You may want to run apt-get update to correct these problems*" ]; then
		{ echo "There is a duplicate sources.list entry, running update again may fix this.  Do you with to run update again? (Y,N,Q)"
		read RESPONSE
		echo "You said: $RESPONSE"
			
			if [ '$RESPONSE' = 'y' ]; then
				echo "updating..."
				sudo apt-get update
			
			else if [ '$RESPONSE' = 'n' ]; then
				echo "upgrading..."
				sudo apt-get upgrade

			else if [ '$RESPONSE' = 'q' ]; then
				echo "exiting..."
				fi

			else echo "I do not understand" #how do I make it look back to asking the question?
		}

	
	elif [ '$UPDATE_OUTPUT' != "*W: You may want to run apt-get update to correct these problems*" ]; then
		sudo apt-get upgrade
	fi

exit
```

---

### Post by mlind on 2006-06-13
You might want to use return values instead, apt-get manual page says that script
returns "decimal 100 on error". You can get this value from bash using $? param.

echo $? ouputs the return value, which will be 100 if there's an error.

---

### Post by Lunar_Lamp on 2006-06-13
Ok, so now the code looks like this:

```
#!/bin/sh
	
sudo apt-get update; echo $?

	if [ '$?' = "100" ]; then
		{ echo "There is a duplicate sources.list entry, running update again may fix this.  Do you with to run update again? (Y,N,Q)"
		read RESPONSE
		echo "You said: $RESPONSE"
			
			if [ '$RESPONSE' = 'y' ]; then
				echo "updating..."
				sudo apt-get update
			
			else if [ '$RESPONSE' = 'n' ]; then
				echo "upgrading..."
				sudo apt-get upgrade

			else if [ '$RESPONSE' = 'q' ]; then
				echo "exiting..."
				fi }

			# else echo "I do not understand" ##how do I make it look back to asking the question?
		#}

	
	elif [ '$?' != "0" ]; then
		sudo apt-get upgrade
	fi

exit
```

I would appreciate it if you could check over my syntax particularly, as I have never scripted anything before, so I may have made a very silly error.

---

### Post by mlind on 2006-06-13
lol, I'm _really_ poor when it comes to shell scripting, but you might go with
something like this

```

#!/bin/sh

if [ "$UID" -ne "0" ]; then
  echo "Root privileges required!"
  exit 1
fi

update() {
  echo "updating..."
  apt-get update $*
}

upgrade() {
  echo "upgrading..."
  apt-get upgrade $*
}


## main 
update

if [ "$?" -eq "0" ]; then
	upgrade
	exit 0
fi

##try to resolve errors
while [ "$?" -eq "100" ]; do
	echo "There is a duplicate sources.list entry, running update again may fix this.  Do you with to run update again? (Y,N,Q)"
	echo -n "> "
	read RESPONSE
	echo "You said: $RESPONSE"

        case $RESPONSE in
	  y)
  		update -f
		;;
	  n)
		upgrade
		;;
	  q)
		echo "exiting..."
		exit 0
		;;
	esac
done

```

---

### Post by Lunar_Lamp on 2006-06-14
Ok, breaking that script down to make sure I understand it (I want to learn bash as well as complete a working script!):

part 1:
 - check's if you are root or not.  I presume "-ne" is just a synonym for "!=", both of which mean "not equal to".

part 2:
```
update() {
  echo "updating..."
  apt-get update $*
}

upgrade() {
  echo "upgrading..."
  apt-get upgrade $*
}

```

This is declaring the variables "update" and "upgrade" to be later used in the script.  Whilst I have never coded in bash or C (or anything else for that matter), I was under the impresion that variable() was a C-style declaration, and BAsh was just different - but I assume you are confident that would work?  The $* just adds on any conditions I enter on the command line (i.e. the names of the packages I want to install)?


Main

This section starts by saying "update", which has already been declared to do apt-get update, and checks that the exit status is 0 (i.e. successful) and then does "apt-get upgrade" and exits.

The error section is self explanatory at first, until we get to "case".  I have NO IDEA at all about the syntax or logic process going on here.  Well, I half do, but I don't uderstand why you made it different to what I did, but I am sure there is a reason.  Syntatically, what on earth are the ;; all about?


On another note, this script (say it was called up 'upgrademe', saved in /bin/bash, and made executable) would need to be executed with sudo command i.e. sudo upgrademe.  Surely it would make more sense to define the update and upgrades to use the sudo command internally?  Or is this seen as a security no-no, even though you would still need to type in the password if you weren't already sudo-authorised?

---

### Post by mlind on 2006-06-14
> **Lunar_Lamp]Ok, breaking that script down to make sure I understand it (I want to learn bash as well as complete a working script!):

part 1:
 - check's if you are root or not.  I presume "-ne" is just a synonym for "!=", both of which mean "not equal to".
[/QUOTE]

Yes. As a good practice, don't put any 'sudo' stuff inside your scripts. On another
system or for other user there might not be sudo possibility. This way it will work,
and test that it's executed as root user. Root user has always $UID 0.

Sudo is just requesting temporary root privileges.

You must test your scripts while you incrementally build those. Just **chmod 700** you script file and then 
```

bash -x ./myscript

```

or even bash -xv ./myscript for more verbose output.


[QUOTE=Lunar_Lamp]
part 2:
```
update() {
  echo "updating..."
  apt-get update $*
}

upgrade() {
  echo "upgrading..."
  apt-get upgrade $*
}

```

This is declaring the variables "update" and "upgrade" to be later used in the script.  Whilst I have never coded in bash or C (or anything else for that matter), I was under the impresion that variable() was a C-style declaration, and BAsh was just different - but I assume you are confident that would work?  The $* just adds on any conditions I enter on the command line (i.e. the names of the packages I want to install)?
[/QUOTE]

Thoses are functions, not variables. $* should maybe be "$*", but you got the
meaning of it, it appends all supplied arguments to the command. Bash function
declaration doesn't contain parameters, just empty ().

[QUOTE=Lunar_Lamp]
The error section is self explanatory at first, until we get to "case".  I have NO IDEA at all about the syntax or logic process going on here.  Well, I half do, but I don't uderstand why you made it different to what I did, but I am sure there is a reason.  Syntatically, what on earth are the  said:**
> 

Switch case is IMO better for multiple if-else clauses and makes code more
readable, logic is same though. Logic is that it will loop that part until there's no
error. Maybe better approach would be that you would declare your own variable
$OK and loop it untill $OK was set to true or something.

I guess ;; means 'break'.

[QUOTE=Lunar_Lamp]
On another note, this script (say it was called up 'upgrademe', saved in /bin/bash, and made executable) would need to be executed with sudo command i.e. sudo upgrademe.  Surely it would make more sense to define the update and upgrades to use the sudo command internally?  Or is this seen as a security no-no, even though you would still need to type in the password if you weren't already sudo-authorised?

Put your own scripts on /usr/local/bin or $HOME/bin, I prefer the latter.

The idea is that you require root privileges, that's what sudo does. Apt-get will
fail as you know when it's not executed as root user, but is better to check this
before running the script, output about error will be more verbose.

(If I were you, I'd just declare aliases to apt-get upate & upgrade tasks.)

---

### Post by Lunar_Lamp on 2006-06-16
Ok, the script doesn't quite work.
It runs the update as expected, but when I get an error it doesn't ask me if I want to redo the "update" like I want it to.  It just exits.

```
<snip>W: Duplicate sources.list entry http://gb.archive.ubuntu.com dapper/main Package s (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386 _Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com dapper/restricted P ackages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_dapper_restricted _binary-i386_Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com dapper/universe Pac kages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_dapper_universe_bin ary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used  instead.

```


The code on my system is this:

```
#!/bin/sh

if [ "$UID" -ne "0" ]; then
  echo "Root privileges required!"
  exit 1
fi

update() {
  echo "updating..."
  apt-get update $*
}

upgrade() {
  echo "upgrading..."
  apt-get upgrade $*
}


## main 
update

if [ "$?" -eq "0" ]; then
	upgrade
	exit 0
fi

##try to resolve errors
while [ "$?" -eq "100" ]; do
	echo "There is a duplicate sources.list entry, running update again may fix this.  Do you with to run update again? (Y,N,Q)"
	echo -n "> "
	read RESPONSE
	echo "You said: $RESPONSE"

        case $RESPONSE in
	  y)
  		update -f
		;;
	  n)
		upgrade
		;;
	  q)
		echo "exiting..."
		exit 0
		;;
	esac
done

```

---

### Post by mlind on 2006-06-16
[QUOTE=Lunar_Lamp]Ok, the script doesn't quite work.
It runs the update as expected, but when I get an error it doesn't ask me if I want to redo the "update" like I want it to.  It just exits.
[/QUOTE]

Yeah, because successful update on the while loop will return 0, which will pass
the while clause.

How about this
```

#!/bin/sh

if [ "$UID" -ne "0" ]; then
  echo "Root privileges required!"
  exit 1
fi

update() {
  echo "updating..."
  apt-get update $* > **/dev/null**
}

upgrade() {
  echo "upgrading..."
  apt-get upgrade $*
}


## main 
update

#trivial case
if [ "$?" -eq "0" ]; then
        upgrade
        exit 0
fi

##try to resolve errors
RESOLVED="false"
while [ $RESOLVED = "false" ]; do
	echo "There is a duplicate sources.list entry, running update again may fix this.  Do you with to run update again? (Y,N,Q)"
        echo -n "> "
        read RESPONSE
        echo "You said: $RESPONSE"

        case $RESPONSE in
          Y | y)
                update -f
                ;;
          N | n)
		upgrade
		RESOLVED="true"
		;;
          Q | q)
                echo "exiting..."
                RESOLVED="true"
                ;;
        esac
done

```

---

### Post by Lunar_Lamp on 2006-06-18
I'll try that, the problem is it's slightly frustrating to test this script, as I don't know what causes the "duplicate sources" error, so am not sure how to trigger it.  I have edited the script now, and shall return if there any problems!

---

### Post by mlind on 2006-06-18
[QUOTE=Lunar_Lamp]I'll try that, the problem is it's slightly frustrating to test this script, as I don't know what causes the "duplicate sources" error, so am not sure how to trigger it.  I have edited the script now, and shall return if there any problems![/QUOTE]

If you want to test it, you must comment out the "trivial case part" and modify
the script (invert conditions) so you can test every path of execution. I doubt that
bash supports mocking, like object oriented languages like Python do.

---

### Post by aysiu on 2006-06-18
How often do you change your sources.list that you need a script to check if there are duplicate sources? Just curious.

---

### Post by Lunar_Lamp on 2006-06-19
Personally, I change it regularly, but I find that my sources list seems to have 'duplicate entries' more often than should be warranted by my editing of the sources list (though having never used a debian based distro before I cannot say for sure).

This was partly an excercise in learning to script in bash however, to solve a minor problem I had identified.  I've learnt a fair amount of the basics in the process of trying to work it out myself, so it has had a reasonable level of success.

I ran the script this morning, and it told me initially there were bzip errors with some of the sources, so I ran it again (as prompted - that worked!), it told me there were duplicate sources still.  So I quit (retrospectively I wish I had allowed it to run through just once more), and manually did a "sudo apt-get update", which went without a hitch.  So now I am going to have to work out if there is an error with the script or not - the hard part, heh.

---

