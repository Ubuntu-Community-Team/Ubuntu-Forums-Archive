---
title: "send email notifications in nagios"
date: 2010-07-20
forum: General Help
---

### Post by LayTech on 2010-07-20
Hello.

i wanna send email notifications when the servers' services gone down. i have installed nagios successfully in ubuntu 9.10.

in the **contacts.cfg**, i added this :

define contact{
        contact_name                    nagiosadmin             ; Short name of user
        use                             generic-contact         ; Inherit default values from generic-contact template (defined above)
        alias                           Nagios Admin            ; Full name of user
        host_notifications_enabled      1
        service_notifications_enabled   1
        host_notification_period        24x7
        service_notification_options    w,u,c,r
        host_notification_options       d,u,r
        service_notification_commands   notify-service-by-email
        host_notification_commands      notify-host-by-email


        email                           [email]myemail@hotmail.com[/email]   
}

for the *contacts_grou*p in **contacts.cfg**, i add this :

define contactgroup {
        contactgroup_name       admins
        alias                   Nagios Administrators
        members                 nagiosadmin
        }


for the **windows.cfg**, i added this:

define host{
      use                    generic-host
      host_name              qauser-863c2d42
      alias                  qauser-863c2d42
      address                172.20.130.71

      check_command          check-host-alive
      max_check_attempts     10

      notification_interval  120
      notification_period    24x7
      notification_options   d,u,r
      contact_groups         admins
      notifications_enabled  1
}

in **commands.cfg**, i changed the /bin/mail to the following:

# 'notify-host-by-email' command definition
define command{
        command_name    notify-host-by-email



        command_line    /usr/bin/printf "%b" "***** Nagios *****\n\nNotification Type: $NOTIFICATIONTYPE$\nHost: $HOSTNAME$\nState: $HOSTSTATE$\nAddress: $HOSTADDRESS$\nInfo: $HOSTOUTPUT$\n\nDate/Time: $LONGDATETIME$\n" |/usr/bin/mail -s "** $NOTIFICATIONTYPE$ Host Alert: $HOSTNAME$ is $HOSTSTATE$ **" $CONTACTEMAIL$
        }

# 'notify-service-by-email' command definition
define command{
        command_name    notify-service-by-email
        command_line    /usr/bin/printf "%b" "***** Nagios *****\n\nNotification Type: $NOTIFICATIONTYPE$\n\nService: $SERVICEDESC$\nHost: $HOSTALIAS$\nAddress: $HOSTADDRESS$\nState: $SERVICESTATE$\n\nDate/Time: $LONGDATETIME$\n\nAdditional Info:\n\n$SERVICEOUTPUT$" | /usr/bin/mail -s "** $NOTIFICATIONTYPE$ Service Alert: $HOSTALIAS$/$SERVICEDESC$ is $SERVICESTATE$ **" $CONTACTEMAIL$

        }


i have installed postfix too..

what else am i missing? i cant receive email in my email inbox even though the services of the windows server which i'm monitoring are down...

p/s: i have googled for countless of times..it seems i'm on the right track, but what doesn't it work?

please help, thanks lots.

---

### Post by LayTech on 2010-07-20
any help? x.x

---

