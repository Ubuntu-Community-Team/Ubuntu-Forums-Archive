---
title: "HOWTO Nagios disk error fix,different ssh port , and .htpasswd protected apache2"
date: 2011-05-04
forum: General Help
---

### Post by mhgsys on 2011-05-04
*OK^ Maybe I need a better title but this is actually what this "howto" includes.*

I've just installed and configured Nagios , and for all who are having some troubles fixing everything to be up and OK I'm writing down what I have done to make it all work for me.
[B]
In my case;[/B]
**My apache2 is password protected with a .htpasswd file, and my ssh  is hosted on a different port then port 22.**
so I got this http error; > [COLOR="Red"]SERVICE ALERT: localhost;HTTP;WARNING;HARD;4;HTTP WARNING: HTTP/1.1 401 Authorization Required[/COLOR] 
and this ssh error:
> [COLOR="Red"]SERVICE ALERT: localhost;SSH;CRITICAL;HARD;4;Connection refused[/COLOR]

And I got this disk error: > [COLOR="Red"]DISK CRITICAL - /home/user/.gvfs is not accessible: Permission denied[/COLOR]



So..

Here is what I did to make it work; **I've bolded it out to make it clearer to read.. also; I** used vim** , _but you could use nano or even gedit_

[COLOR="Blue"]The HTTP error fix
--------------[/COLOR]
[B]
sudo vi /etc/nagios-plugins/config/http.cfg[/B]

```
# 'check_http' command definition
define command{
        command_name    check_http
        command_line    /usr/lib/nagios/plugins/check_http -H '$HOSTADDRESS$' -I '$HOSTADDRESS$' **-a username:password** '$ARG1$'

        }
```

[COLOR="Blue"]*change 'username: password' to your username and password you use in the .htpasswd file put the password in as plain text so not encrypted like in the .htpasswd file itself*[/COLOR]
 [B]__________________________________________________________________________
[/B]

[COLOR="Blue"]the SSH Connection refused error fix;[/COLOR]
--------------------------------
**sudo vi /etc/nagios3/conf.d/services_nagios2.cfg**

```
# check that ssh services are running
define service {
        hostgroup_name                  ssh-servers
        service_description             SSH
        check_command                   **check_ssh_port!60!server**
        use                             generic-service
        notification_interval           0 ; set > 0 if you want to be renotified
```

[COLOR="Blue"]*port 60 is an example, change it to your ssh port*[/COLOR]

[B]__________________________________________________________________________
[/B]
[COLOR="Blue"]**And the headbreaking DISK CRITICAL - /home/user/.gvfs is not accessible: Permission denied error fix:**[/COLOR]
--------------------------------------------------------------------------
**sudo vi /etc/nagios-plugins/config/disk.cfg**
```
# 'check_disk' command definition
define command{
        command_name    check_disk
        command_line    /usr/lib/nagios/plugins/check_disk -w '20%' -c '10%'  -p '/dev/sda1'   -i '.gvfs'
        }

# 'check_all_disks' command definition
define command{
        command_name    check_all_disks
        command_line    /usr/lib/nagios/plugins/check_disk -w '20%'  -c '10%'  -e  -p '/dev/sda1'  -i '.gvfs' 
        }
```

*-w stands for warning , -c stands for critical*



[SIZE="3"][COLOR="Blue"]**I hope I did not forget to put anything else down I've configured to make this all work for me, and hope that this information is useful for other users[**[/COLOR][/SIZE]

---

