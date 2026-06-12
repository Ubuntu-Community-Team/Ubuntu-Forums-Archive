---
title: "need help with ddclient .conf for dynamic DNS"
date: 2011-08-24
forum: General Help
---

### Post by tetsu7 on 2011-08-24
im having some trouble with my ddclient configuration. i followed the guide from [https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS) and everything seems to be in order however it doesnt work. ive been emailing support at easydns.com however they have yet to offer me a viable solution. perhaps someone here may know what my problem is. below is the results of the command: sudo ddclient -daemon=0 -debug -verbose -noquiet 
below  that is my .conf  i appreciate any advice anyone can offer!

----------------------------------------------------------------------------------------------------------------------------------------------------------------------
/media$  sudo ddclient -daemon=0  -debug -verbose -noquiet
WARNING:  file /var/cache/ddclient/ddclient.cache, line 4: Invalid Value for keyword 'ip' = ''
=== opt ====
opt{cache}                           : <undefined>
opt{cmd}                             : <undefined>
opt{cmd-skip}                        : <undefined>
opt{daemon}                          :  0
opt{debug}                           : 1
opt{exec}                            : <undefined>
opt{facility}                        : <undefined>
opt{file}                            : <undefined>
opt{force}                           :  <undefined>
opt{fw}                              : <undefined>
opt{fw-login}                        : <undefined>
opt{fw-password}                     : <undefined>
opt{fw-skip}                         : <undefined>
opt{geturl}                          :  <undefined>
opt{help}                            : <undefined>
opt{host}                            : <undefined>
opt{if}                              : <undefined>
opt{if-skip}                         :  <undefined>
opt{ip}                              : <undefined>
opt{login}                           : <undefined>
opt{mail}                            : <undefined>
opt{mail-failure}                    : <undefined>
opt{max-interval}                    :  2592000
opt{min-error-interval}              : 300
opt{min-interval}                    : 30
opt{options}                         : <undefined>
opt{password}                        : <undefined>
opt{pid}                             : <undefined>
opt{postscript}                      :  <undefined>
opt{priority}                        : <undefined>
opt{protocol}                        : <undefined>
opt{proxy}                           : <undefined>
opt{query}                           : <undefined>
opt{quiet}                           :  0
opt{retry}                           : <undefined>
opt{server}                          : <undefined>
opt{ssl}                             : <undefined>
opt{syslog}                          : <undefined>
opt{test}                            :  <undefined>
opt{timeout}                         : <undefined>
opt{use}                             : <undefined>
opt{verbose}                         : 1
opt{web}                             : <undefined>
opt{web-skip}                        : <undefined>
=== globals  ====
globals{daemon}                      : 60
globals{debug}                       : 1
globals{login}                       : tetsu7
globals{password}                    : mypassword
globals{pid}                         : /var/run/ddclient.pid
globals{protocol}                    :  dyndns2
globals{quiet}                       : 0
globals{server}                      : api.cp.easydns.com
globals{ssl}                         : 1
globals{use}                         : web
globals{verbose}                     : 1
globals{web}                         :  checkip.dyndns.com/
globals{web-skip}                    : IP Address
=== config ====
config{uneedafix.com}{atime}         : 0
config{uneedafix.com}{backupmx}      : 0
config{uneedafix.com}{cacheable}     : ARRAY(0x853fc38)
config{uneedafix.com}{cmd}           : <undefined>
config{uneedafix.com}{cmd-skip}      : 
config{uneedafix.com}{custom}        : 0
config{uneedafix.com}{fw}            : 
config{uneedafix.com}{fw-login}      : <undefined>
config{uneedafix.com}{fw-password}   :  
config{uneedafix.com}{fw-skip}       : 
config{uneedafix.com}{host}          : uneedafix.com
config{uneedafix.com}{if}            : ppp0
config{uneedafix.com}{if-skip}       : 
config{uneedafix.com}{ip}            : <undefined>
config{uneedafix.com}{login}         : tetsu7
config{uneedafix.com}{max-interval}  : 2592000
config{uneedafix.com}{min-error-interval} : 300
config{uneedafix.com}{min-interval}  : 30
config{uneedafix.com}{mtime}         : 0
config{uneedafix.com}{mx}            : 
config{uneedafix.com}{password}      : mypassword
config{uneedafix.com}{protocol}      : dyndns2
config{uneedafix.com}{server}        : api.cp.easydns.com
config{uneedafix.com}{static}        : 0
config{uneedafix.com}{status}        : 
config{uneedafix.com}{use}           : web
config{uneedafix.com}{warned-min-error-interval} : 0
config{uneedafix.com}{warned-min-interval} : 0
config{uneedafix.com}{web}           : checkip.dyndns.com/
config{uneedafix.com}{web-skip}      : IP Address
config{uneedafix.com}{wildcard}      : 0
config{uneedafix.com}{wtime}         : 30
=== cache  ====
cache{Current}{atime}                : 1314054762
cache{Current}{backupmx}             : 0
cache{Current}{custom}               : 0
cache{Current}{host}                 : Current
cache{Current}{mtime}                : 0
cache{Current}{mx}                   : 
cache{Current}{static}               : 0
cache{Current}{status}               :  notfqdn
cache{Current}{warned-min-error-interval} : 0
cache{Current}{warned-min-interval}  : 0
cache{Current}{wildcard}             : 0
cache{Current}{wtime}                : 30
cache{uneedafix.com}{atime}          : 1314202472
cache{uneedafix.com}{backupmx}       : 0
cache{uneedafix.com}{custom}         : 0
cache{uneedafix.com}{host}           : uneedafix.com
cache{uneedafix.com}{mtime}          : 0
cache{uneedafix.com}{mx}             : 
cache{uneedafix.com}{static}         :  0
cache{uneedafix.com}{status}         : noconnect
cache{uneedafix.com}{warned-min-error-interval} : 0
cache{uneedafix.com}{warned-min-interval} : 0
cache{uneedafix.com}{wildcard}       : 0
cache{uneedafix.com}{wtime}          : 30
DEBUG:    proxy  = 
DEBUG:    url    = checkip.dyndns.com/
DEBUG:    server = checkip.dyndns.com
CONNECT:  checkip.dyndns.com
CONNECTED:  using HTTP
SENDING:  GET / HTTP/1.0
SENDING:   Host: checkip.dyndns.com
SENDING:   User-Agent: ddclient/3.8.0
SENDING:   Connection: close
SENDING:   
RECEIVE:  HTTP/1.1 200 OK
RECEIVE:  Content-Type: text/html
RECEIVE:  Server: DynDNS-CheckIP/1.0
RECEIVE:  Connection:  close
RECEIVE:  Cache-Control: no-cache
RECEIVE:  Pragma: no-cache
RECEIVE:  Content-Length: 105
RECEIVE:  
RECEIVE:   <html><head><title>Current IP  Check</title></head><body>Current IP Address:  67.166.141.37</body></html>
DEBUG:    get_ip: using web, checkip.dyndns.com/ reports 67.166.141.37
WARNING:  skipping update of uneedafix.com from <nothing> to 67.166.141.37.
WARNING:   last updated <never> but last attempt on Wed Aug 24 09:14:32 2011 failed.
WARNING:   Wait at least 5 minutes between update attempts.
-----------------------------------------------------------------------------------------------------------------------------------------------------
# Configuration file for ddclient generated by debconf
#
#  /etc/ddclient.conf

daemon=300
#cache=/tmp/ddclient.cache
pid=/var/run/ddclient.pid
ssl=yes
use=web, web=checkip.dyndns.com/, web-skip='IP Address'
login=tetsu7
password='mypassword'
protocol=dyndns2
#use=if, if=etho
server=api.cp.easydns.com
#wildcard=YES
uneedafix.com
#custom=yes, uneedafix.com

---

### Post by gmargo on 2011-08-24
Take a look at the output of "ddclient --help" - it's 459 lines of help, which includes a section on easydns.  You likely have to change the protocol line to "protocol=easydns" at least.

There's also this bit which uses easydns in an example: [http://www.debianadmin.com/ddclient-update-ip-addresses-at-dynamic-dns-service.html](http://www.debianadmin.com/ddclient-update-ip-addresses-at-dynamic-dns-service.html)

---

