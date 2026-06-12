---
title: "Postfix for a small simulation network"
date: 2012-02-08
forum: General Help
---

### Post by gioannou on 2012-02-08
Hallo all

I have a small 4-stations(with a Virtual guest in each one - so 8 in total)network with all stations connected through a hub. Each station has a static IP in the range 10.0.0.1-10.0.0.8.

I am trying to make a simulation scenario where I will have background traffic in the network. I have been given a script that sends mail to a mail address(mail transmission will be the actual background traffic). The mail address is actually the only parameter that I can change within the script. The script calls the *mail* command to send an email to a given recipient.

My aim is to send emails from each station to another. I have been told that I should create local mailboxes in each station; so if I am getting this right, each station should be running a Postfix instance that will transmit messages. In addition it will receive messages destined for itself. I have installed Postfix on each of them and set the main.cf parameters as follows:

myorigin = mydomain.com
myhostname = Station'sComputerName.mydomain.com
mydestination = mydomain.com
home_mailbox = Maildir/

I have also added each station's user account to the **mail** group. 
However, when I try to run the script, I get the following error in mail.log: "Host or domain name not found".

I am not really experienced in networking with Linux. However, the stations can ping each other and I have successfully tested similar scenarios (web server, database server).

Please forgive my rather poor description. I would appreciate any help. Thanks in advance.

---

