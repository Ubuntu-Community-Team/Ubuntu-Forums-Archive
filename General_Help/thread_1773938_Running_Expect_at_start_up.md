---
title: "Running Expect at start up"
date: 2011-06-02
forum: General Help
---

### Post by welshmike on 2011-06-02
I have the Expect script below named winnwftp.
How may I run it successfully at start up? I've added a startup program of "expect winnwftp" but the ftp does not update the website. Could this be because I don't have an internet connection at start up when "expect winnwftp" runs? 

```
#!/bin/expect
# Proper header for a expect script.

# Testing 
# Run as root, of course.???

send "ftp starting.....\n"

# create new file how?
# use existing /home/mike/update.html

# start and run ftp process
spawn ftp winchesternw.org.uk
expect ":"
send "*userid*\r"
expect "Password:"
send "*password*\r"
expect "ftp>"
send "put /home/mike/update.html /public_html/update.html\r" 
expect "ftp>"
send "bye\r"
```

---

### Post by TeoBigusGeekus on 2011-06-03
You could add a sleep command at the beginning of your script, so that your network has time to go up before the script commands are invoked.

---

### Post by welshmike on 2011-06-03
> **TeoBigusGeekus said:**
> You could add a sleep command at the beginning of your script, so that your network has time to go up before the script commands are invoked.

Good thinking Teo and thanks.
My boyfriend suggested that today at the Soton beer fest.

---

### Post by TeoBigusGeekus on 2011-06-03
> **welshmike said:**
> ...Soton beer fest.

Me likes...

---

