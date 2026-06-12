---
title: "How to Uninstall Avira Help me"
date: 2011-02-11
forum: General Help
---

### Post by shankar4u007 on 2011-02-11
I have installed Avira in this way.

> 
o get started, click here and download Avira AntiVir Personal for Linux.

 

antivir_mav

 

After downloading, go to Places –> Downloads.

 

antivir_mav_1

 

Then right-click on the package and select ‘Extract Here’.

 

antivir_mav_3

 

After extracting go to Applications –> Accessories –> Terminal and run the command below and press Enter.

cd Downloads/antivir-workstation-pers-<version #>

antivir_mav_4

 

Then type the command below and press Enter to begin installing.

sudo ./install

antivir_mav_5

 

Read the license and press [Y] to continue.

 

antivir_mav_6

 

During the installing, accept all prompts set to [Y] and press Enter.

 

antivir_mav_7

 

When prompted to check for updates once a week, type [Y] and press Enter.

 

antivir_mav_8

 

Also type [Y] to install AVIRA Guard GNOME plugin.

 

antivir_mav_9

 

Continue until the installation is complete. Once complete, right-click on a blank area of the top panel and select Add to Panel.

 

antivir_mav_10

 

Then select Avira AntiVir Guard (Monitor) and click ‘Add’

 

antivir_mav_11

 

Enjoy!

 

antivir_mav_12

 

Without dazuko support, the umbrella will remain closed but you could still use the on-demand scanning feature of AntiVir.

 

antivir_mav_15

 

To perform a scan on your system, go to Applications –> Accessories –> Terminal and run the command below:

sudo avscan

antivir_mav_16



[COLOR="Red"][SIZE="5"]I am noob., Please help me to REMOVE/UNINSTALL Avira from my PC[/SIZE][/COLOR]

---

### Post by DanneStrat on 2011-02-12
> After extracting go to Applications &#8211;> Accessories &#8211;> Terminal and run the command below and press Enter.

cd Downloads/antivir-workstation-pers-<version #>

Do the above step again so you get into

the directory where you have your

install/uninstall scripts.

To list which files are in the directory do a

```
ls
```

Now look for an "uninstall" script.

You have to be in the same directory as the script.

Go ahead and do:

```
sudo ./uninstall --product=all
```

If you get any questions in the terminal at this point just 

answer them.

That should be it.

Let me know if it works.:)

---

### Post by williamts99 on 2011-02-12
> **shankar4u007 said:**
> I have installed Avira in this way.
]I am noob., Please help me to REMOVE/UNINSTALL Avira from my PC[/SIZE][/COLOR]

Page 15 of the manual:
[http://www.avira.com/documents/products/pdf/en/man_avira_antivir-unix_prof_en.pdf](http://www.avira.com/documents/products/pdf/en/man_avira_antivir-unix_prof_en.pdf)


```
Uninstalling AntiVir
You can use the uninstall script, located in the temporary AntiVir directory, to remove
Avira AntiVir Server/ Professional. The syntax is:
uninstall [--product=productname] [--inf=inf-file] [--force]
[--version] [--help]
where productname is Guard.
Open the AntiVir directory:
cd /usr/lib/AntiVir/guard
Type:
./uninstall --product=Guard
The script starts uninstalling the product, asking you step by step, if you want to
keep backups for the license file, for the configuration files and logfiles; it can also
remove the cronjobs you made for Guard and Scanner.
Answer the questions with y or n and press Enter.
Avira AntiVir Server/ Professional is removed from your system.

```

Basically:
```
cd /usr/lib/AntiVir/guard
```

```
sudo ./uninstall --product=Guard
```

---

### Post by shankar4u007 on 2011-02-15
Thanks buddy ill check it and tell u buddy....
Thanks for your help...

---

