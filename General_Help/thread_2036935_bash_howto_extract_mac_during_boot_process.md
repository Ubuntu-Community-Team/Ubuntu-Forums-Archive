---
title: "bash: howto extract mac during boot process"
date: 2012-08-03
forum: General Help
---

### Post by go4unkwn on 2012-08-03
hello network experts

i use a clonezilla image to set up about 30 school pc's.
til now after the restore i had to adapt hostname, hosts and interface by hand.

now i try to automat this using a bash script. the bash script will be launched within rc.local.

the bash script should extract the mac address using ifconfig. see below

[HTML]# extract Hardware Adresse
    mac=$(/sbin/ifconfig | grep ^eth* | tr -s ' ' | cut -d' ' -f6 | tr "[a-z]" "[A-Z]")[/HTML]the mac address then is used in a case statement. see below some fragments of the script:

[HTML]    # set network interface, hostname, hosts
    case "${mac}" in
        00:00:00:00:00:00)
            echo "foo-1" > /etc/hostname
            sed -i '2d' /etc/hosts
            sed -i '2 a\127.0.1.1   foo-1' /etc/hosts
            ;;
        22:22:22:22:22:22)
            echo "foo-2" > /etc/hostname
            sed -i '2d' /etc/hosts
            sed -i '2 a\127.0.1.1   foo-2' /etc/hosts
            sed -i '$d' /etc/network/interfaces
            echo "iface eth0 inet static" >> /etc/network/interfaces
            echo "address 192.168.1.10" >> /etc/network/interfaces
            echo "netmask 255.255.255.248" >> /etc/network/interfaces
            echo "gateway 192.168.1.1" >> /etc/network/interfaces
            echo "dns-nameservers 208.67.222.222 208.67.220.220" >> /etc/network/interfaces
            ;;
        33:33:33:33:33:33)
            echo "foo-3" > /etc/hostname
            sed -i '2d' /etc/hosts
            sed -i '2 a\127.0.1.1   foo-3' /etc/hosts
            sed -i '$d' /etc/network/interfaces
            echo "iface eth0 inet static" >> /etc/network/interfaces
            echo "address 192.168.2.10" >> /etc/network/interfaces
            echo "netmask 255.255.255.248" >> /etc/network/interfaces
            echo "gateway 192.168.2.1" >> /etc/network/interfaces
            echo "dns-nameservers 208.67.222.222 208.67.220.220" >> /etc/network/interfaces
            ;;
        *)
            # all pc's with unkown hardware address stay unchanged
            exit 0
            ;;
    esac
[/HTML]now the problem is when rc.local launches the bash script the mac address seems not to exists then, so the case statement *) is always used..

run i the script in a terminal after login into a user account the script works as expected.

i tried to use a sleep (for 60 seconds) statement before launching the script. it didn't help.

how can i get the mac during the boot process?

any hint is welcome!

kind regards, go4unkwn

---

### Post by Lars Noodén on 2012-08-03
In the second script I would add a debugging statement to print out ${mac} so you can visually verify that it is not empty.  It could be empty.  You can remove it later once things are working.

Also, for grabbing the MAC address, you might use [awk](http://manpages.ubuntu.com/manpages/precise/en/man1/awk.1posix.html), it will be shorter:

```

/sbin/ifconfig eth0 | awk '$4 == "HWaddr" { print $5}'

```

---

### Post by go4unkwn on 2012-08-07
replacing ifconfig with ethtool solved the problem ($mac empty string).

kind regards

---

### Post by claracc on 2012-08-07
As you got your problem fixed, please mark the thread as solved with the "thread tools" in the right upper part of the page.

---

