---
title: "Password Protect printing"
date: 2010-10-23
forum: General Help
---

### Post by Fromanator on 2010-10-23
I help out at a student group, and we offer free printing up to a certain amount, but people love to print way more than we allow. So right now they have to ask for how many pages they need and we put it in the printer, but this is a huge hassle. Anyway the printer is a Lexmark e360dn, there is no way to achieve this setting from the printer itself. Currently it is connected as a network printer using tcp/ip through port 9100 (raw). Right now the computers have windows 7 on them, but recently they have had a lot of problems with viruses from not keeping stuff up to date, and all of the USB drives from all walks of life that get plugged into them. Being able to password protect the printer would definitely add to persuading them to use GNU/Linux.

What I would like:
A password prompt to allow printing, a nice message about why would be sweet but not necessary, to be done locally at each machine, or I could have 1 computer set-up as a CUPS server.

My ideas:
Use the firewall to require a password to establish a connection to the printer (probably possible but I am not sure on how to do it).
Have the the computer reserved for the staff be a CUPS server and somehow control the flow of printing.

Any ideas to get the ball rolling or to point me in the right direction/information would be great. I am tired of having to reformat their computers and keep it up to date as best as I can, to see it get owned by someone's flash drive anyway, GNU/Linux would definitely make my role easier.

Thank you

---

### Post by DaniOcean1776 on 2010-12-13
I have a similar problem.

I work for a small retail company and we recently switched to Ubuntu 10.4. Our floor managers need to print invoices on the check out printers. Consultants, however, tend to print there too and this is turning in to a big hustle for our clients, because the printers load is skyrocketing. You can imagine how frustrating is for you to wait on the check out, because some Joe is printing his/her /insert useless junk here/.

Is there a way to limit the access to the printers by asking for a password before printing? I was thinking of a second profile, just for our managers, but the switch time is too high (they need to switch to their profile, enter our ERP program, find the client in the register and print his invoice). It will be much easier to print directly from their curent profile and just enter a password for printing.

---

