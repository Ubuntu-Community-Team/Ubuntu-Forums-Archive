---
title: "Perl configuration problem in connection with procmail call"
date: 2010-04-22
forum: General Help
---

### Post by Weisswurst on 2010-04-22
Hi!

I have following setup on a ubuntu machine.
- Fetchmail collects emails and notifies procmail
- Procmail forwards this mail to a perl script which extracts the attachments
- then this script executes the bugzilla importxml.pl with the attachments.

This works like a charm on the ubuntu machine. Unfortunately I now have been forced to rebuild this setup on a oracle linux.

Well, I can run the imports from terminal as root user. The import works well.

But if fetchmail trigges procmail and the the perl scripts become executet I get following error:

```

'oracle' is not a valid choice for $db_driver in localconfig: Can't load 'lib/i386-linux-thread-multi/auto/DBD/Oracle/Oracle.so' for module DBD::Oracle: libclntsh.so.10.1: cannot open shared object file: No such file or directory at /usr/lib/perl5/5.8.8/i386-linux-thread-multi/DynaLoader.pm line 230.
at Bugzilla/DB/Oracle.pm line 41
Compilation failed in require at Bugzilla/DB/Oracle.pm line 41.
BEGIN failed--compilation aborted at Bugzilla/DB/Oracle.pm line 41.
Compilation failed in require at (eval 97) line 3.

```

Well, as I said I can run this script manually from terminal. DBD::Oracle is installed twice. Once in the Bugzilla environment and once in /usr/lib/perl5...
The Oracle.so file is also twice on the harddisc.

The path "lib/i386-linux-thread-multi/auto/DBD/Oracle/Oracle.so" is right if you go from the importxml.pl but if perl realy looks on this as absolute path to oracle.so then its clear that the file is not there...

Again. The script works if I call it manually. So whats the difference between manual call and call through the process described at the beginning? Something seems to be different in the perl environment.

The .procmailrc lies in /root and fetchmail is startet manually by the root user in the terminal (for testing). So I thing at the end its in both ways the same user who calls importxml.pl...

I'm grateful for any help, even for suggestions to whom else I could take my question. I'm asking here because I normally use Ubuntu whenever and wherever it's possible...

---

### Post by Weisswurst on 2010-04-23
No ideas?

---

### Post by iponeverything on 2010-04-23
Ugly solution, but have you tried copying Oracle.so to somewhere like /usr/lib/ to see if it gets picked up.

---

### Post by Weisswurst on 2010-04-23
just tried it.
but not even this ugly trick does it :(

---

### Post by Weisswurst on 2010-04-23
I changed the importxml.pl script. Now the path is correct but the error stays the same.

/var/www/bugzilla/lib/i386-linux-thread-multi/auto/DBD/Oracle/Oracle.so is available I even chmodded that file... 

```

'oracle' is not a valid choice for $db_driver in  localconfig: Can't load '/var/www/bugzilla/lib/i386-linux-thread-multi/auto/DBD/Oracle/Oracle.so' for module DBD::Oracle: libclntsh.so.10.1: cannot open shared object file: No such file or directory at /usr/lib/perl5/5.8.8/i386-linux-thread-multi/DynaLoader.pm line 230.
 at Bugzilla/DB/Oracle.pm line 41
Compilation failed in require at Bugzilla/DB/Oracle.pm line 41.
BEGIN failed--compilation aborted at Bugzilla/DB/Oracle.pm line 41.
Compilation failed in require at (eval 97) line 3.


```

---

### Post by iponeverything on 2010-04-23
> 'oracle' is not a valid choice for $db_driver in  localconfig: Can't load '/var/www/bugzilla/lib/i386-linux-thread-multi/auto/DBD/Oracle/Oracle.so' for module DBD::Oracle: libclntsh.so.10.1: cannot open shared object file: No such file or directory at /usr/lib/perl5/5.8.8/i386-linux-thread-multi/DynaLoader.pm line 230.
 at Bugzilla/DB/Oracle.pm line 41


Didn't realize this was one long line.

What is at /usr/lib/perl5/5.8.8/i386-linux-thread-multi/DynaLoader.pm line 230?

```
cat /usr/lib/perl5/5.8.8/i386-linux-thread-multi/DynaLoader.pm |awk 'NR == 230 {print $0}'
```

---

### Post by Weisswurst on 2010-04-23
cat /usr/lib/perl5/5.8.8/i386-linux-thread-multi/DynaLoader.pm |awk 'NR == 230 {print $0}'
  
  my $libref = dl_load_file($file, $module->dl_load_flags) or


Could it be that the libclntsh.so is the real problem?

---

### Post by iponeverything on 2010-04-23
does ```
locate libclntsh.so
```

return anything?

If it does, is it in the libpath?

---

### Post by Weisswurst on 2010-04-23
locate returns

/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/lib/libclntsh.so
/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/lib/libclntsh.so.10.1


but I'm not sure if it's in the lib path when the perl script is active.

Do you know what the option perl -T does? The import script demands to be run with -T...

---

### Post by iponeverything on 2010-04-23
> **Weisswurst said:**
> locate returns

/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/lib/libclntsh.so
/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/lib/libclntsh.so.10.1


but I'm not sure if it's in the lib path when the perl script is active.

Do you know what the option perl -T does? The import script demands to be run with -T...

-T reports security problems. 

quick and dirty test would be drop libclntsh.so.10.1 into /usr/lib

the correct fix if the above works, would be to make sure that

```
/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/lib/ 

```

is in the LD_LIBRARY_PATH for the program's environment.

---

### Post by Weisswurst on 2010-04-23
WUAAAH got it!

Some Env variables weren't right.
I put in a shell script in the process and set some envs and now it works.

tried to set the envs in the importxml.pl
but this didn't work :(

Not to mention, I didn't had this problems on Ubuntu...

---

