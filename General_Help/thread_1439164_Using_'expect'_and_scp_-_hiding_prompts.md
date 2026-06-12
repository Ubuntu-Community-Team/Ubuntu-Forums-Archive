---
title: "Using 'expect' and scp - hiding prompts"
date: 2010-03-25
forum: General Help
---

### Post by BillRebey on 2010-03-25
I'm using a small "expect" script to automate password entry for some file copying.

The automation works fine, but the "Password: " prompt still displays on the screen.  How do I hide the prompts so the user doesn't see "Password: " on the console?

Here's the relevant section of my script:

```

expect -c "spawn /usr/bin/scp -q $2 user@$1:$2
		set timeout 60
		expect {
		    "*password:*" { send myPassword\n; interact }
		    eof { exit }
		    timeout { puts \n--TIMEOUT!--\n;exit}
		}
		exit
	    "

```

---

### Post by ju2wheels on 2010-03-25
Try redirecting all i/o streams to /dev/null...

 /usr/bin/scp -q $2 user@$1:$2 &> /dev/null

---

### Post by BillRebey on 2010-03-26
Thanks for the reply, but 

A) That doesn't work in the context of the "spawn" arguemnt to "expect"

B) I'm pretty sure that if it did work, it would defeat the whole purpose of "expect" and prevent "expect" from receiving  the "password:" prompt.

I need to know how to get "expect" to stifle the display;  not how to supress the message from being sent by the client.

---

### Post by ju2wheels on 2010-03-26
```

log_user 0

```

Set it to 1 to enable output again.

---

### Post by BillRebey on 2010-03-26
Thanks!  

That did the trick.  My only nit-pick is that I still get an extra blank line printed where the "Password:" prompt would have been.  Do you have any idea how to suppress that extra line feed?

---

### Post by ju2wheels on 2010-03-26
Not sure as the doc I read said that should suppress all the output (got it from Exploring Expect by Oreilly btw)...

Shouldnt that first case be this though?:
```

-re ".*password:.*" { send "myPassword\r"; interact }

```

#edited newline with \r

---

### Post by BillRebey on 2010-03-26
Yes, you're right...I forgot the second '.' before the '*'.  Good catch!  I thought it might help, but no luck.

It still didn't fix the problem of the additional line feed.  I've tried changing the end of the expression from ".*" to ".*\r", ".*\n", and ".*$", and nothing works.

Anyone else have any idea why I'm getting the extra linefeed?

---

### Post by ju2wheels on 2010-03-26
See if the quoting within quotes is causing any issue by turning this into an expect script and running it that way, instead of inline...

File test.exp:
```

#!/usr/bin/expect

set hostName [lindex $argv 0]
set filePath [lindex $argv 1]

spawn /usr/bin/scp -q "$filePath" "user@$hostName:$filePath"
set timeout 60
expect {
 -re ".*password:.*" { send "myPassword\n"; interact }
  eof { exit }
  timeout { puts "\n--TIMEOUT!--\n";exit}
}
exit

```

Then run:
```

./test.exp host file

```

Just curious to see if its kicking out those \n's somewhere because you are doing it inline or whether its coming from scp terminating...

---

### Post by psusi on 2010-03-26
Putting your password in a script kind of defeats the purpose of having one.  You should be using ssh-agent to cache the password so you only have to enter it once, rather than writing it down in a script where anyone can find it.

---

### Post by GooeyPeach on 2010-04-07
I found this bit in the man pages that suggests interact may be the culprit.
I have yet to find a way to circumvent this.

> 
During  interact,  previous use of log_user is ignored.  In particular, interact will force its output to be logged (sent to the standard output) since it is presumed the user doesn't wish to interact blindly.


---

