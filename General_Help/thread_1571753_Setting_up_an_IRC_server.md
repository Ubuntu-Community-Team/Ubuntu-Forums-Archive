---
title: "Setting up an IRC server"
date: 2010-09-10
forum: General Help
---

### Post by thegodfaza on 2010-09-10
I've been trying to set up an IRC server and have been having trouble at every turn. I finally went with ircd-ircu as it works out of the box and the config looks simple. I've been trying to find some documentation for how the config file works but even the coder-com.undernet.org site doesn't have any documentation. The example I have found tell me to use config lines like U:*@*:etc but my config file looks like this:
I'd also like to set up services such as NickServ, ChanServ, etc.
```
General {
         name = "localhost.localdomain";
         description = "Debian's ircd default configuration at localhost";
         numeric = 1;
};

Admin {
  Location = "Debian's ircd default configuration at localhost";
  Location = "Please edit your ircd.conf file";
  Contact = "root@localhost";
};

Class {
 name = "Local";
 pingfreq = 1 minutes 30 seconds;
 sendq = 160000;
 maxlinks = 100;
 usermode = "+iw";
};

Class {
 name = "Other";
 pingfreq = 1 minutes 30 seconds;
 sendq = 160000;
 maxlinks = 400;
};

Client {
 host = "*@*";
 ip = "*@*";
 class = "Other";
};

motd {
 host = "*";
 file = "ircd.motd";
};

Jupe {
 nick = "A,B,C,D,E,F,G,H,I,J,K,L,M,N,O,P,Q,R,S,T,U,V,W,X,Y,Z,{,|,},~,-,_,`";
 nick = "EuWorld,UWorld,UWorld2";
 nick = "login,undernet,protocol,pass,newpass,org";
 nick = "StatServ,NoteServ";
 nick = "ChanSvr,ChanSaver,ChanServ";
 nick = "NickSvr,NickSaver,NickServ";
 nick = "LPT1,LPT2,COM1,COM2,COM3,COM4,AUX";
};

Port { port = 6667; };

features {
 "LOG" = "SYSTEM" "FILE" "ircd.log";
 "LOG" = "SYSTEM" "LEVEL" "CRIT";
};
```

---

