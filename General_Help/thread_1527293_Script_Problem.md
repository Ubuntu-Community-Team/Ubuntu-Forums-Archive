---
title: "Script Problem"
date: 2010-07-09
forum: General Help
---

### Post by wynand2020 on 2010-07-09
Hi, can somebody maybe help me with my "if" statement? It's probably just a bracket or something stupid missing, but I cant get the variable "type" to add the line when its selected:


clear
read -p "Please Enter Printer Name      :       " name
read -p "Please Enter Printer IP        :       " IP
read -p "Please Enter Printer Description       :       " des
read -p "Please Enter Printer Location  :       " loc
read -p "Please Enter Printer Class     :       " clas

read -p "Is this a jetdirect or a lpd printer?  :       " type

if [ $type = jetdirect ]
        then $type{socket://$IP:9100}
elif [ $type = lpd ]
        then $type{lpd://$IP/$name}
fi

/usr/sbin/lpadmin -p $name -E -D $des -L $loc -c $clas -v $type -m textonly.ppd

---

### Post by CannibalZerg on 2010-07-09
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)
First of all look at p.4 and p.9

---

### Post by KeyserSoze93 on 2010-07-09
= is assignment. i.e. n=5 sets the variable n equal to 5.

== or -eq checks whether something is equal - presumably what you want.

if [[ $type == "jetdirect" ]]; then ...

---

