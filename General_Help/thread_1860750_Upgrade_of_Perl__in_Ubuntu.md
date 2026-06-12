---
title: "Upgrade of Perl  in Ubuntu"
date: 2011-10-15
forum: General Help
---

### Post by sandip250382 on 2011-10-15
Pals, I have installed Ubuntu 11.10 in my laptop. It has Perl 5.10.1 installed in it . Now I want to upgrade it to Latest Perl version 5.14.2. . I have downloaded perl-5.14.2.tar.gz from Perl website and extracted it . But I am not able to upgrade to it in my system .I searched many online technical notes , tried to implemented the steps still not succeeded. Any help regarding this will be highly appreciated.

---

### Post by Gyokuro on 2011-10-15
Hi,

you have downloaded the perl source package (you have to compile it) and it's not recommended to replace your distro perl!!! You should install a separate perl in /opt/perl and then export the new perl path in your .bashrc (export PATH=/opt/perl/bin:$PATH in your .bashrc) or use perlbrew from CPAN which allows you to manage multiple perl versions.

---

### Post by sandip250382 on 2011-10-15
> **Gyokuro said:**
> Hi,
 
you have downloaded the perl source package (you have to compile it) and it's not recommended to replace your distro perl!!! You should install a separate perl in /opt/perl and then export the new perl path in your .bashrc (export PATH=/opt/perl/bin:$PATH in your .bashrc) or use perlbrew from CPAN which allows you to manage multiple perl versions.
 
[COLOR=black][FONT=Verdana]Thanks for  your reply . How will I install perl seperately  in /opt/perl in Ubuntu, I alreay went through the steps but did not able to perform the process .I already tried to use perlbrew but not sure about the steps . It will be great if you can kindly elaborate on this. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Appreciate your assistance.[/FONT][/COLOR]

---

### Post by Gyokuro on 2011-10-15
In case you compile it yourself you have to install development tools and libs:

sudo apt-get install build-essential

unpack the downloaded perl source archive

tar xzvf perl-5.14.2.tar.gz

configure perl (in the unpacked perl dir):

./Configure -Dprefix=/opt/perl -des
make
make install

and copy/append this content in your .bashrc
export PATH=/opt/perl/bin:$PATH

and for perlbrew look here:

[http://www.perlbrew.pl/](http://www.perlbrew.pl/)

-HTH

---

