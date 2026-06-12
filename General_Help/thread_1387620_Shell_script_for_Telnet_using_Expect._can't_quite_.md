---
title: "Shell script for Telnet using Expect. can't quite find the good tutorial for that"
date: 2010-01-22
forum: General Help
---

### Post by Elie-M on 2010-01-22
I need to open a telnet session using a shell script that follows this format:

telnet 10.100.0.1
expect "Password:"
send <password>
expect "10.100.1>"
send "en"
expect "Password:"
send <password>
expect "10.100.1#"
send "pen" (till the end of lines generated as in |more.... usually we use like 8 space bar buttons after "pen" to generate all)
and I want to redirect the whole generated result of "pen" to results.txt

can anyone help with that? and thxx a lot.

---

### Post by Elie-M on 2010-06-20
i will use my own thread to not create a new one..

I've been working since a little on expect and i've come to a point where I can't quite catch the trick. so some help will be appreciated. the script is:

#!/usr/bin/expect
spawn telnet 10.100.0.1
expect "Password: "
send "password\r"
expect "CMTS>"
send "en\r"
expect "Password: "
send "password#1\r"
expect "CMTS#"

the result till here is that I get to CMTS# and the script terminates.


After the CMTS# prompt I want 2 things to happen:

1st - I want to take control of the script and do whatever command I want from keyboard.
2nd - I want the script to never close/end unless I manually do so.

can anyone help?

---

### Post by gmargo on 2010-06-20
Add the expect command "interact" with no arguments.  Gleaned from the **expect(1)** man page and tested successfully.

---

### Post by Elie-M on 2010-06-21
> **gmargo said:**
> Add the expect command "interact" with no arguments.  Gleaned from the **expect(1)** man page and tested successfully.

Love u man! solved thx very much!

---

