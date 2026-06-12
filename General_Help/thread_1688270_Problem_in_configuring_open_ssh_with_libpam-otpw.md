---
title: "Problem in configuring open ssh with libpam-otpw"
date: 2011-02-15
forum: General Help
---

### Post by bravo13 on 2011-02-15
Hi all,

I have installed installed openssh-server,libpam-otpw,otpw-bin

generated otpw passwords 

edited /etc/pam.d/ssh

added two lines and commented one line
#@include common-auth
auth required pam_otpw.so
session optional pam_otpw.so


edited /etc/ssh/sshd_config 
UsePrivilegeSeparation yes   changed to UsePrivilegeSeparation no
ChallengeResponseAuthentication yes

restarted ssh server

/etc/init.d/ssh restart 

now when i am trying to login using "ssh 127.0.0.1"
it is not using the otpw password , i am not able to login using my normal password .


Thanks in advance

---

### Post by bravo13 on 2011-02-17
I am able to Configure ssh with libpam-otpw

Initially otpw module was not being loaded by ssh for authentication due to an ubuntu bug
[https://bugs.launchpad.net/ubuntu/+source/otpw/+bug/247190](https://bugs.launchpad.net/ubuntu/+source/otpw/+bug/247190)

the error in loading can be found in /var/log/auth.log

there is a workaround for this bug by adding the -fno-stack-protector options while compiling the otpw package. So instead of using apt-get to install libpam-otpw manually download and compile.


Steps in compiling and configuring otpw in ubuntu

1. Download otpw from [http://www.cl.cam.ac.uk/~mgk25/download/]("http://www.cl.cam.ac.uk/%7Emgk25/download/")
2. Extract tar -xvzf otpw-1.3.tar.gz
3. Install the required library modules for compilation 
     libpam0g - Pluggable Authentication Modules library
     libpam0g-dev - Development files for PAM
4. Edit the otpw Makefile in the extracted folder and make, 
    change the line "CFLAGS=-O -ggdb -W -Wall"
    to              "CFLAGS=-O -ggdb -W -Wall -fno-stack-protector"

5. Edit the /etc/pam.d/sshd file as below
   #added by bmathews
    auth       required     pam_otpw.so
    session    optional     pam_otpw.so

   # Standard Un*x authentication. below line commented by bmathews
   #@include common-auth

6. Edit the /etc/ssh/sshd_config by turning on challenge response protocol and enable usage of PAM 
   ChallengeResponseAuthentication yes
   UsePAM yes (yes by default)

7. Generate passwords using pam-gen and put the generated passwords in ".otpw" file in the required users home folder

8. restart ssh deamon "/etc/init.d/ssh restart" 

9. connect using ssh client "ssh user@127.0.0.1"

after these steps ssh connection prompted for a password number as expected and logged me in.

---

