---
title: "help installing this.. plz make a streesed guy happy:("
date: 2006-02-13
forum: General Help
---

### Post by njzillest on 2006-02-13
im so stressed ive been trieng this.. im trieng to make a virtual server. if you can help me, ill give you the adress to download some stuff.. 

you can also im me on AIM my screen name is njzillest101

the directions are here

[http://files.hamachi.cc/linux/README](http://files.hamachi.cc/linux/README)

if you cant get to the link, then its posted below...

Quick Start

	Run 'make install' and then 'tuncfg' from under the root account

	Run 'hamachi-init' to generate crypto identity (any account).

	Run 'hamachi start' to launch Hamachi daemon.

	Run 'hamachi login' to put the daemon online and to create an account.

	Run 'hamachi join <network>' to join the network.

	Run 'hamachi go-online <network>' to go online in the network.

	Run 'hamachi list' to list network members and their status.


Installation

	Hamachi Linux client comes as a single executable binary (hamachi)
	compiled for the platform of your choice. This binary includes the 
	daemon, the control application and the setup utility.

	To install hamachi in /usr/bin run the following command from under
	the root account

		make install

	Once installed you must run 'tuncfg' daemon with root privileges -

		sudo /sbin/tuncfg

	or if you don't have sudo -

		su - ; /sbin/tuncfg; exit

	Hamachi requires one time initialization (per Linux user account).
	This step generates cryptographic key pair and creates ~/.hamachi 
	directory where Hamachi stores the keys, the configuration and the 
	state. To perform this initialization run

		./hamachi-init

---

