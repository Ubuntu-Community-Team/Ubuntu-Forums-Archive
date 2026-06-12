---
title: "Help with Expect script - wildcard &amp; sending sudo password"
date: 2010-10-01
forum: General Help
---

### Post by SuaSwe on 2010-10-01
Evening all,

I'm trying to write an expect script (my first one ever so be kind!) to log onto my server, send sudo -i, submit my password, perform some actions then log back out, however I am not able to even get past the "sudo -i" part. I've attached the whole script at the bottom of the message but suspect that the problem lies in here:

```

expect {
        -re "*:~$*" {
                send "sudo -i\r"
                send "$sudo_pw\r"
        }
}

```

Basically, what I'm trying to do is to get the script to look for the string :~$ by using the wildcard *, however all I get doing this is:

> 
couldn't compile regular expression pattern: quantifier operand invalid
    while executing
"expect -nobrace -re {*:~$*} {
		send "sudo -i\r"
		send "$sudo_pw\r"
	}"
    invoked from within
"expect {
	-re "*:~$*" {
		send "sudo -i\r"
		send "$sudo_pw\r"
	}
}"


I don't understand what this means and can't find any explanations/guides that pertain to this problem online. :( If I remove the wildcards the script will SSH to the server but will go no further than the initial prompt (presumably as it doesn't recognise it). 

Another query/problem I have is that if I insert other commands, these seem to be sent simultaneously with or before the ones I already have (I guess because the prompt and therefore what I'm telling the server to "expect" remains the same throughout) - is there a way to force them to be sent in a particular order? 

Thanks all!


&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&
**************ENTIRE SCRIPT**************
&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&

```

#!/usr/bin/expect -f

set timeout 10

#Prompt for old server IP
send_tty "Enter previous server LAN IP: "
expect_user -re "(.*)\n"
set prev_IP $expect_out(1,string)

#Prompt for new server IP
send_tty "Enter new server LAN IP: "
expect_user -re "(.*)\n"
set new_IP $expect_out(1,string)

#Prompt for old server URL
send_tty "Enter previous server URL: "
expect_user -re "(.*)\n"
set old_URL $expect_out(1,string)

#Prompt for new server URL
send_tty "Enter new server URL: "
expect_user -re "(.*)\n"
set new_URL $expect_out(1,string)

#Prompt for old Reverse ARP address in format <octet3>.<octet2>.<octet1>
send_tty "Enter previous RARP address: "
expect_user -re "(.*)\n"
set old_RARP $expect_out(1,string)

#Prompt for new Reverse ARP address in format <octet3>.<octet2>.<octet1>
send_tty "Enter previous RARP address: "
expect_user -re "(.*)\n"
set new_RARP $expect_out(1,string)

#Prompt for server sudo password
stty -echo
send_tty "Enter server's sudo password: "
expect_user -re "(.*)\n"
set sudo_pw $expect_out(1,string)
stty echo

#Used for debugging - set to 1 to show output
log_user 1

#Opens SSH session to device
spawn /usr/bin/ssh $new_IP

expect {
	-re "*:~$*" {
		send "sudo -i\r"
		send "$sudo_pw\r"
	}
}

#Close SSH connection
expect eof
#Wait for socket to close correctly
wait

```

---

### Post by SuaSwe on 2010-10-02
Bump?

---

### Post by SuaSwe on 2010-10-02
Has anyone written a script that does send the sudo password successfully, and if so, could you send me an example? :)

---

