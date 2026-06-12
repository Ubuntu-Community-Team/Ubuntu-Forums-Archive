---
title: "Super basic shell scripting issue"
date: 2011-01-24
forum: General Help
---

### Post by triunenature on 2011-01-24
I'm trying to create a super simple shell script, but i cant get a return line...

the shell script looks like this (only the part that matters)

```
yes '' | ssh-keygen
```

The idea being it will put in a blank char. then enter until the program finishes.

The problem is, it only does the first time, the next 2 times i have to hit enter, it requires me to input it manually (which is exactly what i'm trying to avoid)

Any help would be loved.

The full script (if you care):

```

#!/bin/sh
#
# Created by Omega
# 
# First, program creates RSA key, named id_rsa and id_rsa.pub
# Second, program send the public code to requsted server.
#
echo 'Removing old id_rsa key (if applicable)'
rm -rf ~/.ssh/id_rsa.pub
rm -rf ~/.ssh/id_rsa
echo "Creating RSA key"
yes '' | ssh-keygen

# Checking if ssh-kkeygen created requested file
if [ -e ~/.ssh/id_rsa.pub ]
	then
		echo 'Done'
		echo 'Username and Server in: me@server format'
		read var1
		echo 'Port Number? If standard put 22'
		read var2
		ssh-copy-id -i ~/.ssh/id_rsa.pub "-p $var2 $var"
	else
		echo ''
		echo 'ERROR, ssh-keygen did not execute correctly'
		echo 'Retrying...'
		echo ''
		echo 'Please leave all options default (just press enter)'
		ssh-keygen
			if [ -e ~/.ssh/id_rsa.pub ]
				then
					echo 'Done'
					echo 'Username and Server in: me@server format'
					read var1
					echo 'Port Number? If standard put 22'
					read var2
					ssh-copy-id -i ~/.ssh/id_rsa.pub "-p $var2 $var1"
				else
					echo 'ERROR, ssh-keygen did not execute correctly'
					echo 'Quitting'
					exit
fi
fi
# End

```

---

### Post by hawkmage on 2011-01-24
Are you trying to get the ssh-keygen to run without a prompt?  If so try to use the options on the commnd like this:```
ssh-keygen -f ~/.ssh/id_rsa -P ''
```

---

### Post by triunenature on 2011-01-26
Thank you SOOO much

---

