---
title: "Metasploit help"
date: 2010-10-04
forum: General Help
---

### Post by gem1210 on 2010-10-04
I installed Metasploit and all its dependency's and have been getting errors. 

> ubuntu@ubuntu:/opt/metasploit3/msf3$ msfconsole 

                     888                           888        d8b888
                     888                           888        Y8P888
                     888                           888           888
88888b.d88b.  .d88b. 888888 8888b. .d8888b 88888b. 888 .d88b. 888888888
888 "888 "88bd8P  Y8b888       "88b88K     888 "88b888d88""88b888888
888  888  88888888888888   .d888888"Y8888b.888  888888888  888888888
888  888  888Y8b.    Y88b. 888  888     X88888 d88P888Y88..88P888Y88b.
888  888  888 "Y8888  "Y888"Y888888 88888P'88888P" 888 "Y88P" 888 "Y888
                                           888
                                           888
                                           888


       =[ metasploit v3.4.2-dev [core:3.4 api:1.0]
+ -- --=[ 594 exploits - 302 auxiliary
+ -- --=[ 225 payloads - 27 encoders - 8 nops
       =[ svn r10543 updated today (2010.10.04)

resource (/home/ubuntu/.msf3/msfconsole.rc)> db_driver postgresql

resource (/home/ubuntu/.msf3/msfconsole.rc)> db_connect msf_user:My_Password.@127.0.0.1:5432/msf_database
resource (/home/ubuntu/.msf3/msfconsole.rc)> db_workspace -a MyProject
[*] Added workspace: MyProject
/opt/metasploit3/msf3/data/msfweb/vendor/rails/activerecord/lib/active_record/base.rb:1864: command not found: infocmp -C
/opt/metasploit3/msf3/data/msfweb/vendor/rails/activerecord/lib/active_record/base.rb:1864: command not found: infocmp -C -r
/opt/metasploit3/msf3/data/msfweb/vendor/rails/activerecord/lib/active_record/base.rb:1864: command not found: stty size
/opt/metasploit3/msf3/data/msfweb/vendor/rails/activerecord/lib/active_record/base.rb:2036: command not found: infocmp -C -r
/opt/metasploit3/msf3/data/msfweb/vendor/rails/activerecord/lib/active_record/base.rb:2036: command not found: infocmp -C -r
/opt/metasploit3/msf3/data/msfweb/vendor/rails/activerecord/lib/active_record/base.rb:2036: command not found: stty -a
/opt/metasploit3/msf3/data/msfweb/vendor/rails/activerecord/lib/active_record/base.rb:2036: command not found: stty -a
/opt/metasploit3/msf3/data/msfweb/vendor/rails/activerecord/lib/active_record/base.rb:2036: command not found: stty -g
/opt/metasploit3/msf3/data/msfweb/vendor/rails/activerecord/lib/active_record/base.rb:2036: command not found: stty -a
/opt/metasploit3/msf3/data/msfweb/vendor/rails/activerecord/lib/active_record/base.rb:2036: command not found: stty -a
/opt/metasploit3/msf3/data/msfweb/vendor/rails/activerecord/lib/active_record/base.rb:2036: command not found: stty  -echo -icrnl cbreak -ixoff
msf > 
And when I try to run sessions it seems to hang and do nothing.

> msf > sessions -l
/opt/metasploit3/msf3/lib/rex/socket/comm/local.rb:251: command not found: stty 

Active sessions
===============

  Id  Type   Information  Connection
  --  ----   -----------  ----------
  1   shell               192.168.1.100:55476 -> x.x.x.x:22009
  2   shell               192.168.1.100:37119 -> x.x.x.x:4653
  3   shell               192.168.1.100:37977 -> x.x.x.x:20301
  5   shell               192.168.1.100:38200 -> x.x.x.x:26105
  18  shell               192.168.1.100:42602 -> x.x.x.x:28260

/opt/metasploit3/msf3/lib/rex/socket/comm/local.rb:251: command not found: stty -a
/opt/metasploit3/msf3/lib/rex/socket/comm/local.rb:251: command not found: stty -g
/opt/metasploit3/msf3/lib/rex/socket/comm/local.rb:251: command not found: stty -a
/opt/metasploit3/msf3/lib/rex/socket/comm/local.rb:251: command not found: stty -a
/opt/metasploit3/msf3/data/msfweb/vendor/rails/activesupport/lib/active_support/callbacks.rb:180: command not found: stty  -echo -icrnl cbreak -ixoff
msf > sessions -i 18
/opt/metasploit3/msf3/lib/rex/socket/comm/local.rb:251: command not found: stty 
[*] Starting interaction with 18...Any help appreciated.
Thanks

---

### Post by andrewthomas on 2010-10-04
[http://ubuntuforums.org/showthread.php?t=1519644](http://ubuntuforums.org/showthread.php?t=1519644)

---

### Post by gem1210 on 2010-10-04
> **andrewthomas said:**
> [http://ubuntuforums.org/showthread.php?t=1519644](http://ubuntuforums.org/showthread.php?t=1519644)

Thanks andrewthomas
It didnt work, I still get the same errors.
I tried install framework 3.2 and it works.  [http://www.metasploit.com/releases/framework-3.2.tar.gz](http://www.metasploit.com/releases/framework-3.2.tar.gz)

---

