---
title: "Multiple PHP versions on one Apache2 installation"
date: 2010-10-06
forum: General Help
---

### Post by Nerijus on 2010-10-06
Hello, 

Anybody know how to run multiple PHP versions on one Apache2 installation?

I need that for development purposes, as for example some sites does not work with PHP 5.3 and I need PHP 5.2 to be able to work on that website (upgrading code to PHP 5.3 is not a solution in this case).

I have found many and many tutorials for Windows, Mac, but nothing for Linux (Ubuntu). I know there should be a way how I would be able to switch between PHP versions very easily.

As I understand the best way to reach this goal would be to run PHP 5.3 as Apache module and other PHP versions as CGI. But how do I do that on Ubuntu?

Thanks in advance for someone who could show me the path and help me to solve this head ache!

---

### Post by Nerijus on 2010-10-06
Anybody? This is really urgent... :confused:

---

### Post by zitch on 2010-10-06
Here's an old article for running PHP4 and PHP5 on Apache2 at the same time on older Debian 3.1 and Ubuntu 5.10 systems: [http://www.howtoforge.com/apache2_with_php5_and_php4](http://www.howtoforge.com/apache2_with_php5_and_php4)

It might give you some ideas on how to set things up, but getting both PHP 5.2 and PHP 5.3 installed is one step that escapes me.

My own solution was to run Ubuntu 8.04.4 Server with its own Apache2 - PHP 5.1 system (which matched a client's server setup) in VirtualBox and use SSHFS to link the VM environment to my development setup.  I'll probably use a newer Ubuntu setup down the road when I need PHP 5.2 installed.

---

