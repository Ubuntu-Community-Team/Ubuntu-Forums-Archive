---
title: "Shell Acript Help"
date: 2012-07-30
forum: General Help
---

### Post by Vishal Agarwal on 2012-07-30
Hi, 
I have created the below shell script:

> 
#!/bin/bash
TotalData=$(grep dove /var/log/auth.log | grep "authentication failure" | awk '// {print $13 "," $14}' | replace "ruser=" "" | replace "rhost=" "")
$(iptables -F input-pop-hack-blocked)
for i in $TotalData
do
        UserName=$(echo $i | cut -d"," -f 1)
        UserIp=$(echo $i | cut -d"," -f 2)
        echo "UserName = $UserName , UserIp = $UserIp "
        if [ -d "/home/$UserName" ]; then
                {
                (echo "User $UserName Exist")
                }
        else
                {
                (echo "User $UserName does not Exist")
                if [$(iptables -L input-pop-hack-blocked -vn | grep $UserIp)]; then
                        {
                        (echo "iptables -A input-pop-hack-blocked  -i eth1 -s $UserIp -p tcp --dport 110 -j DROP")
                        $(iptables -A input-pop-hack-blocked  -i eth1 -s $UserIp -p tcp --dport 110 -j LOG --log-level 4 --log-prefix " FW POP $UserIP DROP")
                        $(iptables -A input-pop-hack-blocked  -i eth1 -s $UserIp -p tcp --dport 110 -j DROP)
                        $(echo "iptables -A input-pop-hack-blocked  -i eth1 -s $UserIp -p tcp --dport 110 -j DROP") >> /var/log/HackPopAuthMessage
                        }
                else
                        {
                        (echo " IP Address $UserIp  for Username $UserName aleeady added to firewall ")
                        }
                fi
                }
        fi
done
I am getting the following error.

> ./HackPopAuth: line 17: []: command not found
Seeking help to resolve this problem.
Any help welcome.

---

### Post by Vaphell on 2012-07-30
what's up with all these {} ()? and captured commands doing nothing? o.O
this code doesn't look like your average shell script at all



[COLOR="blue"]_[/COLOR] = space here
```
if [[COLOR="Blue"]_[/COLOR]<stuff>[COLOR="Blue"]_[/COLOR]]
```

error is located here:
```
if [$(iptables -L input-pop-hack-blocked -vn | grep $UserIp)]; then
```

---

### Post by Vishal Agarwal on 2012-07-30
Thanks for the reply.

i am sorry; I did not get your point. I can understand this is some very basic error; but I am facing this for long and did not get the logic for the same. 

It will be a great help if you can hemp me in a bit detailed manner.

Thanks again.

---

### Post by Vishal Agarwal on 2012-07-30
Hi Thanks for your reply again. I got the solution here 
[http://www.linuxcommand.org/wss0100.php](http://www.linuxcommand.org/wss0100.php)


thanks again

---

