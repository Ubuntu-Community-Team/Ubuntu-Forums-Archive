---
title: "Local repository doesn't seem to work after update"
date: 2012-07-12
forum: General Help
---

### Post by mr.akik on 2012-07-12
Hi,
I'm using ubuntu12.04. 
I've created a local offline repository this way:

sudo mkdir -p /usr/local/mydebs
sudo cp /var/cache/apt/archives/*.deb /usr/local/mydebs
cd /usr/local/mydebs
dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz

Then I added this line on /etc/apt/sources.list file :
deb file:/usr/local/mydebs ./

Then I update repository using this command:
sudo apt-get update

I can easily install my previously downloaded packages using apt-get.
But after I use this command with internet connection :
sudo apt-get update
, my local repository doesn't seem to work.
For example :
 I have all the dependencies of the package "wammu" in my local source
(/usr/local/mydebs).
But when I try to install wammu with "sudo apt-get install wammu" command,
it says I've to download 12.5 mb, but I have those packages in my /usr/local/mydebs
directory that it wants to download.
I can now understand that apt-get is using the other mirrors like multiverse, universe,
main etc before it checks my local mirror.
Please tell me how can I make apt-get to use my local repository at first.
I actually want apt-get to install the existing files first and if necessary it should bring
 packages from internet.
Thanks in advance.

---

