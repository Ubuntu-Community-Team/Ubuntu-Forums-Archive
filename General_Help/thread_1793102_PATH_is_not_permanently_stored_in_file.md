---
title: "PATH is not permanently stored in file"
date: 2011-06-29
forum: General Help
---

### Post by dr_dumb99 on 2011-06-29
I am newbie to UBUNTU. I want to add following variables to PATH. I am doing following steps.

1- I open terminal window.
2- I write following commands :
      export  GOROOT=/home/linux/go/hg
      export  GOOS=linux
      export  GOARCH=386
      export  GOBIN=/home/linux/go/bin

     export PATH=$PATH:$GOBIN
 
When I type following command in terminal window: 
     env | grep '^GO' 

It shows following:        
      GOBIN=/home/linux/go/bin/
      GOARCH=386
      GOROOT=/home/linux/go/hg  
      GOOS=linux

I have tried following command in terminal window
     gedit ~/.bashrc  

and pasted following lines in the end of  file.
     GOROOT=/home/linux/go/hg
     GOOS=linux
     GOARCH=386
     GOBIN=/home/linux/go/bin


My problem is that ,  env is not showing above mentioned variables in  PATH.  Or I am using wrong command to get stored paths or I am storing  my path variables in wrong file ?

Can some one guide me where and how I store above mentioned variables in PATH permanently.

Thanks in advance

---

### Post by Bachstelze on 2011-06-29
You forgot export. ;)

---

