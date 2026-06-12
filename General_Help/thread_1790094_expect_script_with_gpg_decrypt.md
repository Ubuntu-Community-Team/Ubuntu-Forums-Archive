---
title: "expect script with gpg decrypt"
date: 2011-06-24
forum: General Help
---

### Post by mike909 on 2011-06-24
2 part question:
1. does anyone know of a good "bash scripting" forum for posts like these?
2. actual issue:
Trying to automate a login to a device (which does not accept key authentication), using expect, but keeping it secure by encrypting my password with the seahorse (or gpg) agent.
"gpg --decrypt my_file" sends the decyrpted file's contents, in this case my password, to stdout. So I need to have an expect script that basically does the following:
1. expects to see: Password
2. uses the output of "gpg -d my_file" as a variable
3. sends that variable and hits enter, to complete the log in.
This would give me automated log-in, without storing my password in cleartext.

Using ubuntu 11.04, expect ver. 5.44.1.15-4
Typical ssh expect script here: [http://bash.cyberciti.biz/security/expect-ssh-login-script/](http://bash.cyberciti.biz/security/expect-ssh-login-script/)
Launching that yields:
> 
./test.sh 10.248.7.76
spawn ssh root@  
ssh: Could not resolve hostname : Name or service not known
send: spawn id exp6 not open
    while executing
"send -- "$password\r""
    (file "./test.sh" line 13)


---

### Post by furtypajohn on 2011-06-29
You can do the following to set a variable in the Expect script to your password using the output of gpg:

```
set password "gpg -d my_file"
```Then just send $password using Expect later, and it should properly have your password.

Something like this should do the trick:

```

spawn ssh $user@$ipaddress

expect {
  "Password" { 
        send "$password\n" 
        expect {
          "$ " { }
        }
  }
  default {
        send_user "Login failed\n"
        exit
  }
}
```

---

### Post by mike909 on 2011-06-29
Making progress, got the gpg to decrypt and pass only the password to stdout, but still failing on the expect script passing the output of gpg. 
here is the script that works, with password manually entered ("test")
> 

#!/usr/bin/expect -f
set password  "gpg --decrypt --quiet --no-tty bla.pgp"
spawn ssh test@127.0.0.1

expect "password:" {
	send "test\r"
	expect {
	 "$ " { }
	}
}
interact

and here is what happens if I use the variable (putting expect into debug with -d)
> 
mike@mike-ubu-test:~$ ./test.sh 
expect version 5.44.1.15
argv[0] = /usr/bin/expect  argv[1] = -d  argv[2] = ./test.sh  
set argc 0
set argv0 "./test.sh"
set argv ""
executing commands from command file ./test.sh
spawn ssh test@127.0.0.1
parent: waiting for sync byte
parent: telling child to go ahead
parent: now unsynchronized from child
spawn: returns {6090}

expect: does "" (spawn_id exp6) match glob pattern "password:"? no
test@127.0.0.1's password: 
expect: does "test@127.0.0.1's password: " (spawn_id exp6) match glob pattern "password:"? yes
expect: set expect_out(0,string) "password:"
expect: set expect_out(spawn_id) "exp6"
expect: set expect_out(buffer) "test@127.0.0.1's password:"
send: sending "gpg --decrypt --quiet --no-tty bla.pgp\r" to { exp6 }

expect: does " " (spawn_id exp6) match glob pattern "$ "? no


expect: does " \r\n" (spawn_id exp6) match glob pattern "$ "? no
Permission denied, please try again.
test@127.0.0.1's password: 
expect: does " \r\nPermission denied, please try again.\r\r\ntest@127.0.0.1's password: " (spawn_id exp6) match glob pattern "$ "? no
expect: timed out
tty_raw_noecho: was raw = 0  echo = 1
spawn id exp0 sent <\r>
spawn id exp6 sent <\r\nPermission denied, please try again.\r\r\ntest@127.0.0.1's password: >

Permission denied, please try again.
test@127.0.0.1's password: spawn id exp0 sent <\r>
spawn id exp6 sent <\r\nPermission denied (publickey,password).\r\r\n>

Permission denied (publickey,password).
interact: received eof from spawn_id exp6
tty_set: raw = 0, echo = 1
tty_set: raw = 5, echo = 0


---

### Post by furtypajohn on 2011-06-30
Looks like I was wrong before...try this:

```
#!/usr/bin/expect
spawn gpg --decrypt --quiet --no-tty bla.pgp
set lineterminationChar "\r"
expect   {
    $lineterminationChar   { append password $expect_out(buffer);exp_continue}
    eof                    { append password $expect_out(buffer)}
}

puts $password
```

This may help: [http://wiki.tcl.tk/2958](http://wiki.tcl.tk/2958)

---

### Post by mike909 on 2011-07-07
I will try to read through the link, but as of now, still getting the following:
> 
spawn gpg --decrypt --quiet --batch /home/mike/bla.pgp
test
can't read "expect_out": variable is array
    while executing
"append password $expect_out (buffer)"
    invoked from within
"expect {
	$lineterminationChar { append password $expect_out (buffer);exp_continue }
	eof		     { append password $expect_out (buffer) }
	}"
    (file "./test.sh" line 5)


---

### Post by mike909 on 2011-10-25
Attempting new way, this time including expect debugging output.
script (testing ssh'ing to localhost with test user & password):
```

#!/usr/bin/expect -d

set prompt "$ "   ;# our shell or whatever prompt we have
   set command "gpg --decrypt --quiet --batch /home/mike/bla.pgp"

   spawn bash          ;# spawn the bash

   expect "$prompt"    ;# wait for prompt

   send   "$command\r" ;# send command
   expect "$command\r" ;# discard command echo

   expect -re "(.*)\r" ;# match and save the result
        set password "$command"

spawn ssh test@127.0.0.1
        sleep 1
        expect "password: "
        sleep 1 
        send "$password\n"
         
interact

```

Output of expect debug:
> 
mike@mike-ubu-test:~$ ./test.sh
expect version 5.44.1.15
argv[0] = /usr/bin/expect  argv[1] = -d  argv[2] = ./test.sh  
set argc 0
set argv0 "./test.sh"
set argv ""
executing commands from command file ./test.sh
spawn bash
parent: waiting for sync byte
parent: telling child to go ahead
parent: now unsynchronized from child
spawn: returns {9932}

expect: does "" (spawn_id exp6) match glob pattern "$ "? no
mike@mike-ubu-test:~$ 
expect: does "\u001b]0;mike@mike-ubu-test: ~\u0007mike@mike-ubu-test:~$ " (spawn_id exp6) match glob pattern "$ "? yes
expect: set expect_out(0,string) "$ "
expect: set expect_out(spawn_id) "exp6"
expect: set expect_out(buffer) "\u001b]0;mike@mike-ubu-test: ~\u0007mike@mike-ubu-test:~$ "
send: sending "gpg --decrypt --quiet --batch /home/mike/bla.pgp\r" to { exp6 }

expect: does "" (spawn_id exp6) match glob pattern "gpg --decrypt --quiet --batch /home/mike/bla.pgp\r"? no
gpg --decrypt --quiet --batch /home/mike/bla.pgp

expect: does "gpg --decrypt --quiet --batch /home/mike/bla.pgp\r\n" (spawn_id exp6) match glob pattern "gpg --decrypt --quiet --batch /home/mike/bla.pgp\r"? yes
expect: set expect_out(0,string) "gpg --decrypt --quiet --batch /home/mike/bla.pgp\r"
expect: set expect_out(spawn_id) "exp6"
expect: set expect_out(buffer) "gpg --decrypt --quiet --batch /home/mike/bla.pgp\r"
'. Activating booster.rn for '(.*)

expect: does "\n" (spawn_id exp6) match regular expression "(.*)\r"? Gate "*\r"? gate=no
test
mike@mike-ubu-test:~$ 
expect: does "\ntest\r\n\u001b]0;mike@mike-ubu-test: ~\u0007mike@mike-ubu-test:~$ " (spawn_id exp6) match regular expression "(.*)\r"? Gate "*\r"? gate=yes re=yes
expect: set expect_out(0,string) "\ntest\r"
expect: set expect_out(1,string) "\ntest"
expect: set expect_out(spawn_id) "exp6"
expect: set expect_out(buffer) "\ntest\r"
spawn ssh test@127.0.0.1
parent: waiting for sync byte
parent: telling child to go ahead
parent: now unsynchronized from child
spawn: returns {9953}

expect: does "" (spawn_id exp7) match glob pattern "password: "? no
test@127.0.0.1's password: 
expect: does "test@127.0.0.1's password: " (spawn_id exp7) match glob pattern "password: "? yes
expect: set expect_out(0,string) "password: "
expect: set expect_out(spawn_id) "exp7"
expect: set expect_out(buffer) "test@127.0.0.1's password: "
send: sending "gpg --decrypt --quiet --batch /home/mike/bla.pgp\n" to { exp7 }
tty_raw_noecho: was raw = 0  echo = 1
spawn id exp7 sent <\r\n>

spawn id exp7 sent <Permission denied, please try again.\r\r\ntest@127.0.0.1's password: >
Permission denied, please try again.
test@127.0.0.1's password: spawn id exp0 sent <\r>
spawn id exp7 sent <\r\nPermission denied, please try again.\r\r\ntest@127.0.0.1's password: >

Permission denied, please try again.
test@127.0.0.1's password: spawn id exp0 sent <\r>
spawn id exp7 sent <\r\nPermission denied (publickey,password).\r\r\n>

Permission denied (publickey,password).
interact: received eof from spawn_id exp7
tty_set: raw = 0, echo = 1
tty_set: raw = 5, echo = 0

Expect is sending output to the prompt, just not the contents of the decrypted file (bla.pgp).

---

