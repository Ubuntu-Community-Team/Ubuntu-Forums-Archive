---
title: "VMware &amp; 2.6.12-10-386"
date: 2006-03-04
forum: General Help
---

### Post by hdensley on 2006-03-04
Problems with VMware finding C Header Files

Basically VMware's installer can't find linux-headers-2.6.12-10-386 and the whole process is stuck at this point (you can't go forward).

I've seen this posted, but none of the solutions are fully documentated, or don't apply to myself.  I can't get a copy of these source files to direct vmware to.  I'm really really stuck here, and I've wasted probably 5 hours on this.  The killer is this: sudo apt-get install$(uname -r) dosen't solve the problem - nor can I find this version of linux-headers in package manager.

I don't know if it's noteworthy, but I have both ubuntu and kbuntu installed...

Can someone either tell me how to update the kernal(?) or give me some constructive ideas on what to do with my time when I decide to walk away from this seemingly hopeless problem?

---

### Post by patrickfromspain on 2006-03-04
Go to synaptic and download the linux headers for your kernel. If you don't have them.. have you enabled the extra repos? If not: sudo gedit /etc/apt/sources.list and uncomment all the lines starting with deb. Then save, and sudo apt-get update and you can go back into synaptic and search for the headers. They are there, for sure, as I've used them myself.

When done, launch the vmware installer. At the point it asks for the linux headers, you have to give the correct path, enter manually: /usr/src/linux-headers-2.6.12-10 or ...-2.6.12-10-386, I'm not sure know.

hope it helps

---

### Post by fantan on 2006-03-04
Hi,

Before start vmware-uninstall.pl do the following:
sudo gnome-terminal
apt-get install gcc-3.4
CC=/usr/bin/gcc-3.4
export CC
exit
gnome-terminal
CC=/usr/bin/gcc-3.4
export CC
cd /where_the_unpacked_source_is/vmware-distrib
sudo vmware-uninstall.pl (this is a symlink to .../vmware-distrib/bin/vmware-uninstall.pl, which is a script for installing vmware)
It is important, that you should compile vmware with the same version of gcc as the kernel, and this is gcc-3.4!

hello,
fantan

---

### Post by hdensley on 2006-03-04
[QUOTE=patrickfromspain]Go to synaptic and download the linux headers for your kernel. If you don't have them.. have you enabled the extra repos? If not: sudo gedit /etc/apt/sources.list and uncomment all the lines starting with deb. Then save, and sudo apt-get update and you can go back into synaptic and search for the headers. They are there, for sure, as I've used them myself.

When done, launch the vmware installer. At the point it asks for the linux headers, you have to give the correct path, enter manually: /usr/src/linux-headers-2.6.12-10 or ...-2.6.12-10-386, I'm not sure know.

hope it helps[/QUOTE]

I tried this, and this is the output:

:~$ sudo apt-get install$(uname -r)
E: Invalid operation install2.6.12-10-386

and tried this: 
sudo apt-get install linux-headers-2.6.12-10-386
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-2.6.12-10-386


- I get this after running apt-get update.  when I edited those lists of sources (suggested above) I uncommented the backports, everything else is uncommented

---

### Post by hdensley on 2006-03-04
Hi fantan,

Still stuck.  it can't find the packages

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

---

### Post by steharg on 2006-03-04
i installed vmware workstation earlier today and had the same probelm with the gcc and headers 

this solved it for me

> apt-get install gcc-3.4
CC=/usr/bin/gcc-3.4
export CC

and then

> sudo apt-get install linux-headers-2.6.12-10-386


then i ran the vmware installer and it worked fine.

(i didnt have to uncomment any repositries)

---

### Post by hdensley on 2006-03-04
[QUOTE=steharg]i installed vmware workstation earlier today and had the same probelm with the gcc and headers 

this solved it for me



and then



then i ran the vmware installer and it worked fine.

(i didnt have to uncomment any repositries)[/QUOTE]


I wonder if there's a problem with my repositories???

root@ubuntu:/home/hensley/VMware/vm# apt-get install gcc-3.4
Reading package lists... Done
Building dependency tree... Done
gcc-3.4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
root@ubuntu:/home/hensley/VMware/vm# CC=/usr/bin/gcc-3.4
root@ubuntu:/home/hensley/VMware/vm# export CC
root@ubuntu:/home/hensley/VMware/vm# sudo apt-get install linux-headers-2.6.12-10-386
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-2.6.12-10-386
root@ubuntu:/home/hensley/VMware/vm#

---

### Post by hdensley on 2006-03-04
Here's the solution.  You HAVE to change your repositories collection, especially - as in my case - if all the current repositories collections are already uncommented - otherwise you'll never be able to find the linux-header file version to install

1. edit the sources list via terminal: sudo gedit /etc/apt/sources.list
2. re-populate this file with repositories from this site: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
3. run: 'vmware-install.pl' from the directory VMware is currently in
4. C header file are in: /usr/src/linux-headers-2.6.12-10-386/include

Cheers,

---

