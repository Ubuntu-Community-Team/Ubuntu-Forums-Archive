---
title: "Editing .bashrc for Google Go"
date: 2009-11-11
forum: General Help
---

### Post by tledesma on 2009-11-11
NEWBIE Q:

I recently installed Ubuntu 9.10.  And have not yet tinkered with the files.  How do I edit .bashrc in order to accomodate Google's new Go programming language?

**Taken from the Google install page:  **[http://golang.org/doc/install.html](http://golang.org/doc/install.html)


The Go compilation environment depends on three environment variables that you should set in your .bashrc or equivalent, plus one optional variable:

**$GOROOT** 
The root of the Go tree.  Typically this is $HOME/go     but it can be any directory. 

**$GOOS** and **$GOARCH**      
The name of the target operating system and compilation architecture.     
Choices for $GOOS are linux, darwin (Mac OS X 10.5 or 10.6), and nacl (Native Client, an incomplete port).     

Choices for $GOARCH are amd64 (64-bit x86, the most mature port), 386 (32-bit x86), and arm (32-bit ARM, an incomplete port). The valid combinations are     linux/amd64,     linux/arm,     linux/386,     darwin/amd64,     darwin/386,     and     nacl/386.

**<I'm using Ubuntu with 32 bit x86>**

**$GOBIN** (optional)      The location where binaries will be installed.     
If you set $GOBIN, you need to ensure that it  is in your $PATH so that newly built Go-specific     command such as the compiler can be found during the build.     
The default, $HOME/bin, may already be in your $PATH. 

I'm still learning this.  So, I appreciate any help.

Thanks

---

### Post by ncmncm on 2009-11-11
Have you read through basci BASH settings here:
[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_01.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_01.html)

For example, the  $GOROOT can be set by adding this line to the .bashrc file:

> GOROOT=`echo $HOME/go`

---

### Post by BarryNorton on 2009-11-11
Don't put echo into the file. Use echo to append the file, e.g.:

> echo 'export ECHO=$HOME/go' >> .bashrc

---

### Post by Srinivasiyer on 2009-11-12
I have written an article on my Blog on how to install Google GO on Ubuntu 9.10  .Here is the link for the same 

 
[http://www.talkonsomething.com/2009/11/google-go-ubuntu/](http://www.talkonsomething.com/2009/11/google-go-ubuntu/)

Hope this helps :)

Regards,
Srinivas Iyer

---

