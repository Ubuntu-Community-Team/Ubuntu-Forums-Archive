---
title: "Making a cron job to erase 0 byte files out of a group of folders"
date: 2009-07-31
forum: General Help
---

### Post by harry71194 on 2009-07-31
Hello, I am using Ubuntu CLI. I have a python IRC bot running in some lesser-active chans. Rather than messing up my very stable code, I need a way to have a cron job remove 0 byte files every 1 hour. You see, the logging bot makes 1 file every hour, and it is blank until activity happens in the room. No activity happens, I get a blank txt file. They are annoying.

So, how do I have all the 0 Byte blank text files in /var/www/logs/irc/* get erased at the end of every hour? Like *.59 minutes.

Here is an example of the directory structure: harryy.no-ip [dot] biz/logs/irc/hy71194/2009/07/31/22.txt


Help please :D

Edit: here is my code if you would rather help me fix the problem of making the files unless they are needed... Find line "## OUTED BY" to see where I fixed the 'error' or writing "Logs beginning at this time:", but it still makes those darn text files.

```
#! /usr/bin/env python

import os

network = 'irc.freenode.net'
port = 8001
nick = 'IRCLogs'
channels = ['#hy71194','#botters','#linux-il'] # LOWERCASE ONLY
name = 'Harryy Log Bot - http://IRCLogs.no-ip.biz'
password = 'nickservpasswd'

if os.name == 'nt':
    LOG_PATH = 'C:/logs/'
else:
    LOG_PATH = '/var/www/logs/irc/'


__author__ = "Chris Oliver <excid3@gmail.com>"
__version__ = "0.1.0"
__date__ = "05/06/2009"
__copyright__ = "Copyright (c) Chris Oliver"
__license__ = "GPL2"

# Imports
from time import strftime
import irclib
import time

class LogFile(object):
    def __init__(self,path,extention='.txt',constant_write=False,mode=3,new_folders=True):
        # path = path to store ****
        # extention = log extention
        # constant_write = keep the file open inbetween writes or
        #                  open & close it every time.
        # mode = 1/2/3
        #        1 = save file name as time.time() value
        #        2 = save file as a human readable value
        #        3 = save it as "log_file.log"
        self.path = path
        self.mode = mode
        self.keep_open = constant_write
        self.extention = extention
        self.file = None
        self.name = ''
        self._total_name = ''
        self.new_folders=new_folders
        self._init_file()

    def close(self,message=''):
        # close the log file
        if message:
            self.write(message)
        if self.keep_open:
            self.file.close()
        self.keep_open = True
        self.file = None        

    def write(self,message,prefix=True):
        if self.file == None:
            raise Exception('File has been closed douchebag')
        if not self.keep_open:
            self.file = open(self._total_name,'a+')
        if prefix:
            _prefix = '[%s] '%time.strftime('%H:%M:%S')
        else:
            _prefix = ''

        self.file.write(_prefix+message+'\n')

        if not self.keep_open:
            self.file.close()

    def _init_file(self):
        if self.new_folders:
            self.path = self.path + time.strftime("%Y/%m/%d/")
            if not os.path.exists(self.path):
                os.makedirs(self.path)
            
        # Create our ****
        if self.mode == 1:
            self.name = str(time.time())
        elif self.mode == 2:
            self.name = time.strftime("%m-%d-%Y")
        else:
            self.name = time.strftime("%H")

        self._total_name = self.path+self.name+self.extention
        
        if os.path.isfile(self._total_name):
            self.file = open(self._total_name,'a+')
        else:
            self.file = open(self._total_name,'w')
            
## OUTED BY HARRY TODAY        self.write('[IRC logfile - Started %s]'%time.ctime(),False)

class LogFileManager(object):
    def __init__(self,values):
        # Values = list of keys for the LogFiles
        self.value = values
        self.logs = {}
        for value in self.value:
            self.logs[value] = LogFile(LOG_PATH+value[1:]+'/')

    def reload_logs(self):
        for value in self.value:
            self.logs[value] = LogFile(LOG_PATH+value[1:]+'/')

    def write(self,name,text):
        self.logs[name.lower()].write(text)

    def write_all(self,text):
        for log in self.logs:
            self.logs[log].write(text)
    
    def close(self,name):
        self.logs[name.lower()].close()

    def close_all(self):
        for log in self.logs:
            self.logs[log].close()

        
# Connection information

def _real_handler(message,name=None):
    global current_hour,manager
    now_hour = time.strftime('%H')
    if now_hour == current_hour:
        if name:
            manager.write(name,message)
        else:
            manager.write_all(message)
    else:
        current_hour = now_hour
        manager.close_all()
        manager.reload_logs()
        if name:
            manager.write(name,message)
        else:
            manager.write_all(message)

def handleJoin(connection,event): # Join notifications
    _real_handler(event.source().split('!')[0] + ' has joined ' + event.target(),name=event.target())

def handlePart(connection,event): # Join notifications
    _real_handler(event.source().split('!')[0] + ' has left ' + event.target(),name=event.target())

def handlePubMessage(connection, event): # Any public message
    _real_handler(event.source().split ('!')[0] + ': ' + event.arguments()[0], name=event.target())

def handleTopic(connection,event):
    _real_handler(event.source().split( '!' )[0] + ' has set the topic to "' + event.arguments()[0],name=event.target())

def handleQuit(connection,event):
    _real_handler(event.source().split ( '!' ) [ 0 ] + ' has disconnected : ' + event.arguments() [ 0 ])

def handleKick(connection,event):
    if nick == event.arguments() [ 0 ]:
        server.join(event.target())
    _real_handler(event.arguments() [ 0 ] + ' has been kicked by ' +event.source().split ( '!' ) [ 0 ] + ': ' + event.arguments()[ 1 ],name=event.target())

def handleMode ( connection, event ):

   # Channel mode
   if len ( event.arguments() ) < 2:
      _real_handler(event.source().split ( '!' ) [ 0 ] + ' has altered the channel\'s mode: ' + event.arguments() [ 0 ],name=event.target())

   # User mode
   else:
      _real_handler(event.source().split ( '!' ) [ 0 ] + ' has altered '+ ' '.join(event.arguments() [ 1: ]) + '\'s mode: ' + event.arguments()[ 0 ],name=event.target())

def handleNick(connection,event):
    _real_handler(event.source().split('!')[0] +' changed nick to ' + event.target())
    

#(self,path,extention='.log',constant_write=False,mode=2)
manager = LogFileManager(channels)
current_hour = time.strftime('%H')

# Create an IRC object
irclib.DEBUG = 1
irc = irclib.IRC()

irc.add_global_handler('join', handleJoin)
irc.add_global_handler('part',handlePart)
irc.add_global_handler('pubmsg', handlePubMessage)
irc.add_global_handler('topic', handleTopic)
#irc.add_global_handler('quit', handleQuit)
irc.add_global_handler('kick', handleKick)
irc.add_global_handler('mode', handleMode)
#irc.add_global_handler('nick',handleNick)

# Create a server object, connect and join the channel
server = irc.server()
server.connect(network, port, nick, ircname=name)
if password: server.privmsg("nickserv","identify %s"%password)
##server.away("Away, Logging. Ask Harryy for this bot in your chan!")
time.sleep(10)
for channel in channels:
    server.join(channel)

# Jump into an infinte loop
irc.process_forever()
```

---

### Post by harry71194 on 2009-08-01
Blump :D

---

### Post by tokico on 2009-08-01
Edit your crontab (/etc/crontab).
Add a line like this:

```
00 * * * * rm /var/www/logs/irc/*
```

And every hour (21:00, 22:00, 23:00) it should delete the logs.

---

### Post by tokico on 2009-08-01
> **harry71194 said:**
> Blump :D

And it's called bump, not blump. ;)

---

### Post by wojox on 2009-08-01
Set permissions:

```
#! /bin/bash

find /var/www/logs/irc/* -size 0 -type f -exec rm -f '{}' \;
```

Then crontab -e

0 */1   *   *   *    path/to/script

will run every hour.

---

### Post by harry71194 on 2009-08-02
> **tokico said:**
> And it's called bump, not blump. ;)
Hehe, I know :D
> **wojox said:**
> Set permissions:

```
#! /bin/bash

find /var/www/logs/irc/* -size 0 -type f -exec rm -f '{}' \;
```Then crontab -e

0 */1   *   *   *    path/to/script

will run every hour.
Cool. How would I have it run every *:59? I don't want it to erase a file that is in use at the time (ie being written at the beginning of the hour), or not comping the cron job before the hour changes, making a write error on the script.

---

### Post by harry71194 on 2009-10-29
Update: fixed the actual code, and open-sourced it ;) [http://code.google.com/p/pyirclogs/](http://code.google.com/p/pyirclogs/)

---

