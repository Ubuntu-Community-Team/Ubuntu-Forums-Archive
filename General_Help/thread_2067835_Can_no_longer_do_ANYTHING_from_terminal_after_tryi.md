---
title: "Can no longer do ANYTHING from terminal after trying to install/uninstall JAVA"
date: 2012-10-07
forum: General Help
---

### Post by sendittokeith on 2012-10-07
GAWD i hate java.

RESOLVED:  Had to install synaptic and reinstall apt, sudo - and im sure i'll have to do that for anything else thats missing... unless someone knows a better way.  Boooo JRE you suck.

After trying to put 7 jre on my ubuntu 12.04.1 now i can not do ANYTHING from the terminal - apt-get, reboot, sudo, etc -- uptime does work. all return 'command not found' I just rebuilt my ubuntu on Fri and needed the POS Java for one stupid VPN program that i must have.  I am sure it is something like my paths, environment, etc or something, but coming from a win background I am not sure how to fix in UBUNTU - PLEASE HELP.

YUP confirmed that JAVA is the culprite (I hate you java!)

here is output when i tried to remove sudo (was gonna remove/add see if it fixed it)

Here is the output:
installArchives() failed: (Reading database ... 
dpkg: warning: files list file for package `oracle-java7-installer' missing, assuming package has no files currently installed.


....and please for the love of god don't ever develop anything on an O/S that requires the JRE, it kills babies.

---

### Post by hawthornso23 on 2012-10-08
If you are going to try out removing and adding programs via synaptic just to see that you can do it then you should try doing it with programs less vital to the functioning of your system than apt and sudo. Remove and reinstall a silly game or something.

Both sudo and apt are essential for synaptic itself to function. Removing them is thus likely to leave you with a non-functional synaptic and no way to recover. In other words it will pretty effectively trash your system. If you are lucky synaptic will realise that you are asking it to do something incredibly stupid and will refuse to do it. If you are unlucky synaptic will do exactly as you have requested.

I am perplexed that some problem with Java could prompt you to try to do something as drastic as removing apt and sudo.

---

