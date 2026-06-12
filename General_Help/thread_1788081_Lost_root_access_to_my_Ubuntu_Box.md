---
title: "Lost root access to my Ubuntu Box"
date: 2011-06-22
forum: General Help
---

### Post by pamuditha99 on 2011-06-22
1. I was trying to give proper permissions for my new wordpress installtion.
    I gave the command 
    ```
usermod -G www-data Jupitor
```    to add user "Jupitor" to the group "www-data" as advised in somewhere.
    It was executed without any warning and everything seems ok.
    (The only sudoer account on my machine was "Jupitor")
3. Then I logged off and then log in again. Now whenever i try to execute something with sudo the system complians "jupitor is not in the sudoers file.  This incident will be reported"
4. My root account was also disabled since i did everything with sudo command with "Jupitor" account.
5. Now I lost administrative access to my box.
6. How can I recover my root access?

Any help would be highly appreciated since i'm in a deep trouble.

Thanks.

---

### Post by Dangertux on 2011-06-22
Well assuming you have physical access to the box.

You can boot into single user mode as root and correct your mistakes. Alternatively , you can boot to recovery mode off a LiveCD.

You can boot single user mode by doing the following.

Hit esc as the computer is booting to get to the grub menu. Highlight the entry you wish to boot single user press e. 

You will then have the option to edit the boot parameters.

Go to the kernel line and remove quiet splash and append the word single. Press Ctrl+x to boot.

You will now be logged in as root, in a terminal.

---

### Post by sisco311 on 2011-06-22
Boot into *Recovery Mode* and (re-)add your user (Jupitor) to the **admin** group. 

For detailed instructions, see : [http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

EDIT: and next next time before you run a command, check out its man page :evil:

[quote=man usermod]

        -G, --groups GROUP1[,GROUP2,...[,GROUPN]]]
           A list of supplementary groups which the user is also a member of.
           Each group is separated from the next by a comma, with no
           intervening whitespace. The groups are subject to the same
           restrictions as the group given with the -g option.

           [color=red]If the user is currently a member of a group which is not listed,
           the user will be removed from the group.[/color] [b]This behaviour can be
           changed via the -a option, which appends the user to the current
           supplementary group list.[/b]

[/quote]

[quote=man usermod]
       -a, --append
           Add the user to the supplementary group(s). Use only with the -G
           option.

[/quote]

---

### Post by crispy_420 on 2011-06-22
You can also get to rescue mode but holding down shift key before grub loads and it will give you the grub "rescue" option. When you boot into that you are root.

---

