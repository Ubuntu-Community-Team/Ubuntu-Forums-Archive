---
title: "try to install perl 5.8.8 in ubuntu 9.0.4"
date: 2009-11-16
forum: General Help
---

### Post by kingkong22 on 2009-11-16
Hi, 
   I have ubuntu 9.0.4 with perl 5.10.0. But I want to install perl 5.8.8
because of its stablity. I downloaded perl_5.8.8**.deb. I used the command
sudo dkpg -i perl_5.8.88.deb to install it. I got the following error messages:

[C:/home/CS/Desktop] > sudo dpkg -i perl_5.8.8*.deb /usr/local/bin
[sudo] password for CS: 
(Reading database ... 175796 files and directories currently installed.)
Preparing to replace perl 5.8.8-12ubuntu0.4 (using perl_5.8.8-12ubuntu0.4_i386.deb) ...
Unpacking replacement perl ...
dpkg-split: error reading /usr/local/bin: Is a directory
dpkg: error processing /usr/local/bin (--install):
 subprocess dpkg-split returned error exit status 2
dpkg: dependency problems prevent configuration of perl:
 perl depends on perl-base (= 5.8.8-12ubuntu0.4); however:
  Version of perl-base on system is 5.10.0-19ubuntu1.1.
dpkg: error processing perl (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 /usr/local/bin/perl

What did I do wrong ? plz help. Thank you very, very much !!!

---

