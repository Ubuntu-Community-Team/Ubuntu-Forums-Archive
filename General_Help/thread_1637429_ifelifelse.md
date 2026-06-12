---
title: "if/elif/else"
date: 2010-12-04
forum: General Help
---

### Post by jhayes on 2010-12-04
so i have this project, part of it is sorting iptables log files.
i was going to go with dst port# but, a better way was to use the sorting iptables does

IPTABLES-FTP-Traffic
IPTABLES-MAIL-Traffic
IPTABLES-SLAMMER-Traffic
IPTABLES-SSH-Traffic
IPTABLES-trojan-Traffic
IPTABLES-unknown-Traffic
IPTABLES-vnc-Traffic
IPTABLES-WEB-Traffic

i want to make an if/elif/else statement to go through my 191,000 line file and make 8 different files with the lines going to their different files.

the start of the script looks like 

#!/bin/bash

cat messages | while read LINE; do
if [ "`echo $LINE | grep 'IPTABLES-FTP-Traffic`" ];then
        (echo "`echo $LINE`" >> IPTABLES-FTP-Traffic); 
else
        echo (echo "nope"); 
fi


but i get a "ports.sh: 1: Syntax error: Unterminated quoted string"
the messages file my user owns, and is read/writeable. i scp the file from another place. this directory is read/writeable, owned by my user. i loaded this up in notepad++ to take a look, and it looks right to me there also ..
please help

---

### Post by SeijiSensei on 2010-12-04
You appear to be missing a single quote.

```
if [ "`echo $LINE | grep 'IPTABLES-FTP-Traffic`" ]
```

should read

```
if [ "`echo $LINE | grep 'IPTABLES-FTP-Traffic'`" ]
```

with the matching single quote after "Traffic".

That's what "Syntax error: Unterminated quoted string" means; there's a quote that isn't matched correctly.

Sometimes it's easier to use the $() syntax rather than the backtick operator, especially when you have nested quotes.  You don't really need the single quotes around "IPTABLES-FTP-Traffic" either, since it has no embedded spaces.

---

### Post by jhayes on 2010-12-05
thanks. your reply got me motivated to continue to work on it. 
I had gotten 2 lines of code from my teacher that sota did what i needed... but the spirit of the project is to make your own stuff.

so here is version1, writes each line that its finds to file

#!/bin/bash
#get the messages file put in same dir as this
ssh name@x.x.x.x '(sudo cat /var/log/messages; sudo zcat /var/log/messages*gz) | grep "IPTABLES" |tr -s " " | sed -e "s/ DF//"' >ports.lwt
cat ports.lwt | while read LINE; do
if [ "`echo $LINE | grep IPTABLES-FTP-Traffic`" ];then
	(echo "`echo $LINE`" >> IPTABLES-FTP-Traffic);
elif [ "`echo $LINE | grep IPTABLES-MAIL-Traffic`" ];then
        (echo "`echo $LINE`" >> IPTABLES-MAIL-Traffic);  
elif [ "`echo $LINE | grep IPTABLES-SLAMMER-Traffic`" ];then  
        (echo "`echo $LINE`" >> IPTABLES-SLAMMER-Traffic);
elif [ "`echo $LINE | grep IPTABLES-SSH-Traffic`" ];then  
        (echo "`echo $LINE`" >> IPTABLES-SSH-Traffic);
elif [ "`echo $LINE | grep IPTABLES-trojan-Traffic`" ];then  
        (echo "`echo $LINE`" >> IPTABLES-trojan-Traffic);
elif [ "`echo $LINE | grep IPTABLES-unknown-Traffic`" ];then  
        (echo "`echo $LINE`" >> IPTABLES-unknown-Traffic);
elif [ "`echo $LINE | grep IPTABLES-vnc-Traffic`" ];then  
        (echo "`echo $LINE`" >> IPTABLES-vnc-Traffic);
elif [ "`echo $LINE | grep IPTABLES-WEB-Traffic`" ];then  
        (echo "`echo $LINE`" >> IPTABLES-WEB-Traffic);
else
	echo "nope"
	echo "$LINE" >> nope; 
fi;
done


version 2 i gave up on, trying to write the lines to variables, and dump at end.

#!/bin/bash
#attempt to write all lines in if/elif to memory
#dump to file at end
#get the messages file put in same dir as this
ssh name@x.x.x.x '(sudo cat /var/log/messages; sudo zcat /var/log/messages*gz) | grep "IPTABLES" |tr -s " " | sed -e "s/ DF//"' >ports.lwt
IPTABLES_FTP_Traffic=""
IPTABLES_MAIL_Traffic=""
IPTABLES_SLAMMER_Traffic=""
IPTABLES_SSH_Traffic=""
IPTABLES_trojan_Traffic=""
IPTABLES_unknown_Traffic=""
IPTABLES_vnc_Traffic=""
IPTABLES_WEB_Traffic=""
cat ports.lwt | while read LINE; do
if [ "`echo $LINE | grep IPTABLES-FTP-Traffic`" ];then
	IPTABLES_FTP_Traffic="\n $LINE";
elif [ "`echo $LINE | grep IPTABLES-MAIL-Traffic`" ];then
        IPTABLES_MAIL_Traffic="\n $LINE";  
elif [ "`echo $LINE | grep IPTABLES-SLAMMER-Traffic`" ];then  
        IPTABLES_SLAMMER_Traffic="\n $LINE";
elif [ "`echo $LINE | grep IPTABLES-SSH-Traffic`" ];then  
        IPTABLES_SSH_Traffic="\n $LINE";
elif [ "`echo $LINE | grep IPTABLES-trojan-Traffic`" ];then  
        IPTABLES_trojan_Traffic="\n $LINE";
elif [ "`echo $LINE | grep IPTABLES-unknown-Traffic`" ];then  
        IPTABLES_unknown_Traffic="\n $LINE";
elif [ "`echo $LINE | grep IPTABLES-vnc-Traffic`" ];then  
        IPTABLES_vnc_Traffic="\n $LINE";
elif [ "`echo $LINE | grep IPTABLES-WEB-Traffic`" ];then  
        IPTABLES_WEB_Traffic="\n $LINE";
else
	echo "nope" >> nope; 
fi;
echo $IPTABLES_FTP_Traffic >> IPTABLES_FTP_Traffic
echo $IPTABLES_MAIL_Traffic >> IPTABLES_MAIL_Traffic
echo $IPTABLES_SLAMMER_Traffic >> IPTABLES_SLAMMER_Traffic
echo $IPTABLES_SSH_Traffic >> IPTABLES_SSH_Traffic
echo $IPTABLES_trojan_Traffic >> IPTABLES_trojan_Traffic
echo $IPTABLES_unknown_Traffic >> IPTABLES_unknown_Traffic
echo $IPTABLES_vnc_Traffic >> IPTABLES_vnc_Traffic
echo $IPTABLES_WEB_Traffic >> IPTABLES_WEB_Traffic
#post file editing
done

i had a test file with 2 lines per if, should have produced text file with 2 lines in it. but it had 5-6 lines, a break 5-6 lines on down several times over. for now im going with version1. will play with ver 2 later.

---

### Post by SeijiSensei on 2010-12-05
A simpler method might be to use awk to find the key phrase, then act accordingly.  By default, awk breaks up a line into fields using the space character as a delmiter.  I don't know which field has the text you're looking for; let's say it's the sixth element in the line for illustration.  Then you could use:

```

DEST_FILE=$(echo $LINE | awk '{print $6}')
echo $LINE >> $DEST_FILE

```

Another good way to avoid a lot of elif's is to use the "case" command.  All the scripts in /etc/init.d do this to select whether to start, stop, restart, etc., a service.  You'll see a "case $1 in" line followed the options and their associated commands.

---

### Post by DaithiF on 2010-12-05
you could just use grep:

```
for type in FTP MAIL SLAMMER SSH trojan unknown vnc WEB
do
  grep IPTABLES-${type}-Traffic messages > IPTABLES-${type}-Traffic.out
done
```

---

