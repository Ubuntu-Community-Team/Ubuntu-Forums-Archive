---
title: "Run Navicat on Virtualbox using Ubuntu based MySQL server"
date: 2011-09-06
forum: General Help
---

### Post by ekh on 2011-09-06
Hi,

As I have used some hours to get a visual SQL editor running on a MySQL server (version 14.14) on Ubuntu 10.10 64-bit, I post my findings here, in case it can be of any help.

I installed MySQL from Synaptics and selected to run locally on my machine (Lenovo W500).

I have installed MySQL Workbench, which is a free and super program for visual design of a database. You can incrementally build your database model and forward engineer (first time) and synchronize the database to your model.

But as I occasionally need to make quite complex queries (up to one printed page in length) I needed a visual query builder, and found no free program, but Navicat has a 30-day full function trial version. If any of you know a free visual query builder program, please post it here.

I installed Navicat in the virtual MS-XP machine (VirtualBox Version 4.04 r70112), and it did not work right away, I could not connect to the MySQL server on the Ubuntu host.

---------

1'st requirement.

The Virtualbox machine must have a network connection enabled.
In the "Oracle VM VirtualBox Manager" select Network and choose the option Host-only adapter, 'vboxnet0'.


2'nd requirement.

The MySQL server was set to run locally, I needed to allow remote connections. So remote access must be enabled and user privileges granted as explained here:

[http://ubuntuforums.org/showpost.php?p=6045337&postcount=2](http://ubuntuforums.org/showpost.php?p=6045337&postcount=2)


3'rd requirement.

On a Ubuntu terminal use the command:

ifconfig

the 'vboxnet0' should be listed, note the IP address.


4'th requirement.

You need an ODBC connector installed as explained here:
[http://ubuntuforums.org/showpost.php?p=10809700&postcount=4](http://ubuntuforums.org/showpost.php?p=10809700&postcount=4)


5'th requirement.

Open the Navicat program in VirtualBox, then in the menu:

File->New Connection...

You get a dialog.

For 'Host Name/IP Address' enter the IP address you got from the ifconfig command.

Set 'Port' to 3306, which is the default MySQL port.

Enter the user name and password you created under the 2'nd requirement.

Click 'OK'


6'th requirement

....[Edit] It worked, at least until I changed my firewall. So be sure the connection is allowed by the firewall, if installed.


Now you should be able to run Navicat on the MySQL server. at least it works for me.

---

