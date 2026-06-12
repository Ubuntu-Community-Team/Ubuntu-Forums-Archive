---
title: "IRC chat with python not working like i want to."
date: 2012-04-12
forum: General Help
---

### Post by Deo Pal on 2012-04-12
hello every,
I would be very grateful if anyone could guide me the right direction since i am new to python but i know basic in c++ and now opting to do in python.

i have a problem and it is not working as it should i mean the print is not working after this code and sometimes it prints and sometimes it doesn't.
           print ('\r[%s/%s] %s\r\n')%(destination,nick,message)#works but is not printing all the messages that has been sent in the irc chat web server.
            print ('\r[%s] ')% (NickName), #this is not working what so ever.

Here is my source code and sorry it is not that clean O_o either.

#!/usr/bin/python

import socket, sys, string
import os
from time import sleep

NickName = raw_input('Nick Name: ')
sck = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
sck.connect(('irc.anythin.com', 6667))
sck.send('NICK ' + NickName + '\r\n')
sck.send("USER %s %s %s :%s\r\n" % (NickName, NickName, NickName,NickName))
sck.send('JOIN ' + '#room \r\n')
data = ''
data = sck.recv(4096)
print data
while True:
   data = sck.recv(4096)    
   sleep(.0001)
   newpid = os.fork()
   if newpid == 0:
      data = sck.recv(4096)
      print data
      if data.find('PING') != -1:
         sck.send('PONG ' + data.split() [1] + '\r\n')
      elif data.find('PRIVMSG') != -1: 
            nick = data.split('!')[ 0 ].replace(':','') 
        message = ':'.join(data.split (':')[2:]) 
            destination = ''.join (data.split(':')[:2]).split (' ')[-2] 
            print ('\r[%s/%s] %s\r\n')%(destination,nick,message)
            print ('\r[%s] ')% (NickName),
            sys.stdout.flush()
   else:
      pids = (os.getpid(), newpid)
      saymsg = raw_input ('\r[' + NickName + '] ')
      sck.send('PRIVMSG #room : %s\r\n' % saymsg)
      print ('\r[%s] ')% (NickName),#this is also not working
      sys.stdout.flush()

---

### Post by Deo Pal on 2012-04-12
there are indentation but when i post it's coming in the same line

---

### Post by Deo Pal on 2012-04-12
here is a prtscn of my program

---

