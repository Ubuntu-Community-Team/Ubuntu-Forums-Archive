---
title: "CUPS doesn't put anything in my /var/log/cups/page_log"
date: 2009-07-10
forum: General Help
---

### Post by Keithamus on 2009-07-10
I've been trying to get my printer to log the pages it prints.

Unfortunately, I cant get it working. It wont log any info in /var/log/cups/page_log.

```

$ cat /etc/cups/cupsd.conf
#                                                       
#                                                       
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this 
#   file.                                                               
#                                                                       

# Administrator user group...
SystemGroup lpadmin          

# Only listen for connections from the local machine.
Listen *:631                                         
Listen /var/run/cups/cups.sock                       

# Show shared printers on the local network.
Browsing Off                                
BrowseOrder allow,deny                      
BrowseAllow all                             
BrowseAddress @LOCAL                        

# Default authentication type, when authentication is required...
DefaultAuthType Basic                                            

# Restrict access to the server...
<Location />                      
  Order allow,deny                
  Allow 192.168.1.*               
</Location>                       

# Restrict access to the admin pages...
<Location /admin>                      
  Encryption Required                  
  Order allow,deny                     
  Allow 192.168.1.*                    
</Location>                            

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM @LOCAL
  Order allow,deny
  Allow 192.168.1.*
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an administrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-JobCUPS-Move-Job>
    Require user @OWNER @SYSTEM @LOCAL
    Order deny,allow
    Allow 192.168.1.*
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM @LOCAL
    Order deny,allow
    Allow 192.168.1.*
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM @LOCAL
    Order deny,allow
    Allow 192.168.1.*
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM @LOCAL
    Order deny,allow
    Allow 192.168.1.*
</Limit>

  <Limit All>
    Order deny,allow
    Allow 192.168.1.*
  </Limit>
</Policy>

#
#

```

My printer is a Brother DCP 8060
```

$ sudo cat /etc/cups/printers.conf
# Printer configuration file for CUPS v1.3.9
# Written by cupsd on 2009-07-06 12:30
<Printer Printer>
Info Brother Laser DCP8060
Location Syn-Star
DeviceURI smb://192.168.1.102/Printer
State Idle
StateTime 1245415759
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

```

The /var/log/cups/page_log exists with open permissions so it shouldn't have any issues writing to it.

```

$ ls -la /var/log/cups/
drwxr-xr-x  2 root root     4096 2009-07-10 12:08 .
drwxr-xr-x 13 root root     4096 2009-07-10 14:01 ..
-rw-r-----  1 root adm     30100 2009-07-10 15:14 access_log
-rw-r-----  1 root lpadmin   186 2009-07-10 10:05 access_log.1.gz
-rw-r-----  1 root lpadmin   560 2009-07-09 08:07 access_log.2.gz
-rw-r-----  1 root lpadmin   315 2009-07-08 08:07 access_log.3.gz
-rw-r-----  1 root lpadmin  1507 2009-07-07 09:10 access_log.4.gz
-rw-r-----  1 root lpadmin   123 2009-07-06 08:07 access_log.5.gz
-rw-r-----  1 root lpadmin   838 2009-07-05 09:45 access_log.6.gz
-rw-r-----  1 root lpadmin   121 2009-07-04 08:12 access_log.7.gz
-rw-r-----  1 root adm      5177 2009-07-10 14:25 error_log
-rw-r-----  1 root lpadmin    97 2009-07-06 12:30 error_log.1.gz
-rw-r-----  1 root lpadmin   600 2009-07-04 13:26 error_log.2.gz
-rw-r-----  1 root lpadmin   105 2009-06-29 17:13 error_log.3.gz
-rw-r-----  1 root lpadmin   746 2009-06-26 11:31 error_log.4.gz
-rw-r-----  1 root lpadmin   216 2009-06-19 14:09 error_log.5.gz
-rwxrwxrwx  1 root adm         0 2009-07-10 12:08 page_log

```

Any help would be immensely appreciated.

---

### Post by Keithamus on 2009-07-14
Still haven't sussed this one out. It is becoming quite frustrating. Anyone had any ideas?

---

### Post by Totson on 2009-08-12
Hi,

Same issue here.

I also have an hp deskjet printer using hplip : prints are correctly logged to page_logs.

So I guess it's something specific to the brother driver...

Anybody having any clue available ?

---

### Post by Keithamus on 2009-08-12
Is your brother printer connected directly to the machine in question? Mine is connected to a windows machine and shared via Samba, which I was suspecting might be the issue, but if yours is straight into the ubuntu machine then it may be the driver.

---

