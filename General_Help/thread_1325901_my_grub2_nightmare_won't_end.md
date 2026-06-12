---
title: "my grub2 nightmare won't end"
date: 2009-11-13
forum: General Help
---

### Post by Kir_B on 2009-11-13
Please help me out of this grub2 nightmare.

[ Minimal Bash--like line editing is supported.
For the first word, Tab lists possible command
completions. Anywhere else Tab lists the possible
completions of a device/filename. ]

grub>

The text above, is how my computer looks after it boots and that's as far as it gets. This is the result of trying to complete the upgrade from grub legacy to grub2 in my Ubuntu, which was installed as a dual boot alongside vista on a Dell inspiron 531s. The Ubuntu was originally 9.04 Jaunty and then upgraded {well, kind of upgraded} to 9.10 Karmic via the internet. As anyone who has upgraded might know, the upgrade didn't completely deal with grub2. I tried all of the instructions I could find on the net, but couldn't completely finish the installation, leaving me with the "Chainloader" screen and a very slow boot. 

I've been trying to complete the upgrade of grub legacy for two weeks now and i've done too many things to list {it's all a blur}. On my final attempt, I believe that this is the command that got me here:

  -rm -f /boot/grub/menu.lst*

On the first few attempts at upgrading the grub, I noticed that the terminal pointed out this command at the end of the upgrade {or at the end of one of the steps}. I didn't use it on those attempts and they weren't successful. I, at some point read somewhere that grub2 didn't use those files and that they would be no longer necessary. That got me thinking that the old files {/boot/grub/menu.lst*} were messing with the new .cfg files keeping the upgrade from completing itself successfully {I think they're .cfg with grub2}. It booted up into the chainloader before, So I decided to run the command, lost myself in a few other tasks and eventually rebooted to find myself here and feeling like an idiot again. 

I had a bad feeling about running this command, so {I hope Fortunately} I accessed these {5} files and copied them into another document and saved it onto the hard drive. I just accessed them and copied them onto my usb drive. I hope I just simply need to create and/or copy these back to their previous location{s}. I just need a good walkthrough the necessary steps. I'm more than a little leary now.  

I am however, willing to try anything again, as I may have been following bad and/or incomplete instructions leading me into this disaster. I even tried to do a clean Karmic install with both the Alternate and Desktop CD's, but, for some reason I can't get it to boot into full screen mode. With a normal install, I can only see the bottom right 1/4 of the screen in the upper left 1/4 of my monitor. With an install using the Safe graphics mode, I get lots of text that never leads to anything and stops midway through it's process {if I remember correctly, about 40% through detecting files}. At least with 9.04 Jaunty Desktop live CD, I'm able to run the demo off of the Live disc in Safe graphics mode, which is the mode I had to use to install 9.04 Jaunty and then installation went without a hitch. With Karmic, it doesn't get past the text phase.

Please, please, please help me before I really mess things up, provided that I haven't already done so.
                    Thanks a million. Kirby #-o

---

### Post by wojox on 2009-11-13
Use the following two commands to determine the device (drive) and partition of the system you wish to boot.

    

      set
      		

      When set is typed without additional entries the command displays the current GRUB 2 settings.

      ls
      		

      Run ls to see the devices recognized by GRUB 2. Example: (hd0) = sda; (hd0,1)=sda1; (hd1,3)=sdb3

Express Boot to the Most Recent Kernel

Press ENTER after entering each command.

   

      1. set root=(hdX,Y)
      		

      Type with correct X,Y results from the ls command and ENTER. Remember GRUB 2 counts the first drive as 0, the first partition as 1. Example: If the Ubuntu system is on sda5, enter: set root=(hd0,5)

      2. linux /vmlinuz root=/dev/sdXY ro
      		

      (Example: linux /vmlinuz root=/dev/sda3)

      3. initrd /initrd.img
      		

      Selects the latest initrd image.

      4. boot 

      Boot to the latest kernel on the selected partition.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by lmarmisa on 2009-11-13
Hello Kirby,

the upgrade from 9.04 to 9.10 does not change the grub version. Grub2 is installed only in new installations.

I would recommend you to re-install your grub program.

Start your computer from a Ubuntu 9.10 LiveCD and select Try Ubuntu without any change to your computer.

When the start is finshed, open Gparted (System -> Administration -> GParted) and try to locate the Ubuntu partition (probably a File System ext3 or ext4). I will suppose that this partitios is /dev/sda1. If no, please, chage it with the correct device. 

Open a terminal (Applications -> Accessories -> Terminal)

Type the following commands:

sudo bash                     #the system will ask for your password
mount /dev/sda1 /mnt   #May be your device is not /dev/sda1
mount --bind /dev /mnt/dev
chroot /mnt
grub-install /dev/sda     #no number here
update-grub

I hope that you does not get any error on these commands.

That is all.

And now, cross your fingers, shutdown your computer, extract the CD and boot your system again.

The system should be start normally with the new grub loader.

Best regards,

Luis

---

### Post by Kir_B on 2009-11-13
Thanks for the input wojox, but I failed to point out that I'm a newborn linux fanatic that's trying to learn the ways of Linux, but I have only learmt so much in my first month and a half. So you'll have to forgive me if it takes me a while to decipher your post, but i'll try. Is this to be done in a terminal or....

Sorry, took me a while to figure out the editing of my post.

This is what the terminal displays when just "set" is typed, followed by "Enter".

[html]                --temp-dir= --compare-dest= --compress \
                --exclude= --exclude-from= --include= \
                --include-from= --version --daemon --no-detach\
                --address= --config= --port= --blocking-io \
                --no-blocking-io --stats --progress \
                --log-format= --password-file= --bwlimit= \
                --write-batch= --read-batch= --help' -- $cur ))
        ;;
        *:*)
            shell=rsh;
            for ((i=1; i < COMP_CWORD; i++ ))
            do
                if [[ "${COMP_WORDS[i]}" == -@(e|-rsh) ]]; then
                    shell=${COMP_WORDS[i+1]};
                    break;
                fi;
            done;
            if [[ "$shell" == ssh ]]; then
                cur=${cur/\\:/:};
                userhost=${cur%%?(\\):*};
                path=${cur#*:};
                path=${path//\\\\\\\\ / };
                if [ -z "$path" ]; then
                    path=$(ssh -o 'Batchmode yes'                 $userhost pwd 2>/dev/null);
                fi;
                COMPREPLY=($( ssh -o 'Batchmode yes' $userhost             command ls -aF1d "$path*" 2>/dev/null |                 sed -e 's/ /\\\\\\\ /g' -e 's/[*@|=]$//g'                 -e 's/[^\/]$/& /g' ));
            fi
        ;;
        *)
            _known_hosts -c -a;
            _filedir
        ;;
    esac;
    return 0
}
_scp () 
{ 
    local cur userhost path;
    COMPREPLY=();
    cur=`_get_cword ":"`;
    _expand || return 0;
    if [[ "$cur" == *:* ]]; then
        local IFS='    
';
        cur=${cur/\\:/:};
        userhost=${cur%%?(\\):*};
        path=${cur#*:};
        path=${path//\\\\\\\\ / };
        if [ -z "$path" ]; then
            path=$(ssh -o 'Batchmode yes' $userhost pwd 2>/dev/null);
        fi;
        COMPREPLY=($( ssh -o 'Batchmode yes' $userhost                    command ls -aF1d "$path*" 2>/dev/null |                    sed -e "s/[][(){}<>\",:;^&!$&=?\`|\\ ']/\\\\\\\\\\\\&/g"                    -e 's/[*@|=]$//g' -e 's/[^\/]$/& /g' ));
        return 0;
    fi;
    [[ "$cur" == */* ]] || _known_hosts -c -a;
    local IFS='    
';
    COMPREPLY=("${COMPREPLY[@]}" $( command ls -aF1d $cur*                 2>/dev/null | sed                 -e "s/[][(){}<>\",:;^&!$&=?\`|\\ ']/\\\\&/g"                 -e 's/[*@|=]$//g' -e 's/[^\/]$/& /g' ));
    return 0
}
_screen () 
{ 
    local cur prev preprev;
    COMPREPLY=();
    cur=`_get_cword`;
    prev=${COMP_WORDS[COMP_CWORD-1]};
    [ "$COMP_CWORD" -ge 2 ] && preprev=${COMP_WORDS[COMP_CWORD-2]};
    if [ "$preprev" = "-d" -o "$preprev" = "-D" -a "$prev" = "-r" -o "$prev" = "-R" ]; then
        COMPREPLY=($( command screen -ls |                 sed -ne 's|^[''    '']\+\('$cur'[0-9]\+\.[^''    '']\+\).*$|\1|p' ));
    else
        case "$prev" in 
            -[rR])
                COMPREPLY=($( command screen -ls |                 sed -ne 's|^[''    '']\+\('$cur'[0-9]\+\.[^''    '']\+\).*Detached.*$|\1|p' ))
            ;;
            -[dDx])
                COMPREPLY=($( command screen -ls |                 sed -ne 's|^[''    '']\+\('$cur'[0-9]\+\.[^''    '']\+\).*Attached.*$|\1|p' ))
            ;;
            -s)
                COMPREPLY=($( grep ^${cur:-[^#]} /etc/shells ))
            ;;
            *)

            ;;
        esac;
    fi;
    return 0
}
_service () 
{ 
    local cur sysvdir;
    COMPREPLY=();
    prev=${COMP_WORDS[COMP_CWORD-1]};
    cur=`_get_cword`;
    [[ ${COMP_WORDS[0]} != @(*init.d/!(functions|~)|service) ]] && return 0;
    [ $COMP_CWORD -gt 2 ] && return 0;
    [ -d /etc/rc.d/init.d ] && sysvdir=/etc/rc.d/init.d || sysvdir=/etc/init.d;
    if [[ $COMP_CWORD -eq 1 ]] && [[ $prev == "service" ]]; then
        _services;
    else
        COMPREPLY=($( compgen -W '`sed -ne "y/|/ /; \
                s/^.*Usage.*{\(.*\)}.*$/\1/p" \
                $sysvdir/${prev##*/} 2>/dev/null`' -- $cur ));
    fi;
    return 0
}
_services () 
{ 
    local sysvdir famdir;
    [ -d /etc/rc.d/init.d ] && sysvdir=/etc/rc.d/init.d || sysvdir=/etc/init.d;
    famdir=/etc/xinetd.d;
    COMPREPLY=($( builtin echo $sysvdir/!(*.rpmsave|*.rpmorig|*~|functions)));
    if [ -d $famdir ]; then
        COMPREPLY=("${COMPREPLY[@]}" $( builtin echo $famdir/!(*.rpmsave|*.rpmorig|*~)));
    fi;
    COMPREPLY=($( compgen -W '${COMPREPLY[@]#@($sysvdir|$famdir)/}' -- $cur ))
}
_signals () 
{ 
    local i;
    COMPREPLY=($( compgen -A signal SIG${cur#-} ));
    for ((i=0; i < ${#COMPREPLY[@]}; i++ ))
    do
        COMPREPLY[i]=-${COMPREPLY[i]#SIG};
    done
}
_ssh () 
{ 
    local cur prev;
    local -a config;
    COMPREPLY=();
    cur=`_get_cword`;
    prev=${COMP_WORDS[COMP_CWORD-1]};
    case "$prev" in 
        -*c)
            COMPREPLY=($( compgen -W 'blowfish 3des 3des-cbc blowfish-cbc \
               arcfour cast128-cbc' -- $cur ))
        ;;
        -*i)
            _filedir
        ;;
        -*l)
            COMPREPLY=($( compgen -u -- $cur ))
        ;;
        *)
            _known_hosts -a;
            [ $COMP_CWORD -eq 1 ] || COMPREPLY=("${COMPREPLY[@]}" $( compgen -c -- $cur ))
        ;;
    esac;
    return 0
}
_sysctl () 
{ 
    local cur;
    COMPREPLY=();
    cur=`_get_cword`;
    COMPREPLY=($( compgen -W "$(sysctl -N -a 2>/dev/null)" -- $cur ));
    return 0
}
_tar () 
{ 
    local cur ext regex tar untar;
    COMPREPLY=();
    cur=`_get_cword`;
    if [ $COMP_CWORD -eq 1 ]; then
        COMPREPLY=($( compgen -W 'c t x u r d A' -- $cur ));
        return 0;
    fi;
    case "${COMP_WORDS[1]}" in 
        ?(-)[cr]*f)
            _filedir;
            return 0
        ;;
        +([^IZzjy])f)
            ext='t@(ar?(.@(Z|gz|bz?(2)))|gz|bz?(2))';
            regex='t\(ar\(\.\(Z\|gz\|bz2\?\)\)\?\|gz\|bz2\?\)'
        ;;
        *[Zz]*f)
            ext='t?(ar.)@(gz|Z)';
            regex='t\(ar\.\)\?\(gz\|Z\)'
        ;;
        *[Ijy]*f)
            ext='t?(ar.)bz?(2)';
            regex='t\(ar\.\)\?bz2\?'
        ;;
        *)
            _filedir;
            return 0
        ;;
    esac;
    if [[ "$COMP_LINE" == *$ext' ' ]]; then
        tar=$( echo "$COMP_LINE" |             sed -e 's/^.* \([^ ]*'$regex'\) .*$/\1/' );
        untar=t${COMP_WORDS[1]//[^Izjyf]/};
        COMPREPLY=($( compgen -W "$( echo $( tar $untar $tar             2>/dev/null ) )" -- "$cur" ));
        return 0;
    fi;
    _filedir "$ext";
    return 0
}
_tcpdump () 
{ 
    local cur;
    COMPREPLY=();
    cur=`_get_cword`;
    prev=${COMP_WORDS[COMP_CWORD-1]};
    case "$prev" in 
        -@(r|w|F))
            _filedir;
            return 0
        ;;
        -i)
            _available_interfaces -a;
            return 0
        ;;
    esac;
    if [[ "$cur" == -* ]]; then
        COMPREPLY=($( compgen -W '-a -d -e -f -l -n -N -O -p \
            -q -R -S -t -u -v -x -C -F -i -m -r -s -T -w \
            -E' -- $cur ));
    fi
}
_uids () 
{ 
    if type getent >&/dev/null; then
        COMPREPLY=($( getent passwd |                 awk -F: '{if ($3 ~ /^'$cur'/) print $3}' ));
    else
        if type perl >&/dev/null; then
            COMPREPLY=($( compgen -W '$( perl -e '"'"'while (($uid) = (getpwent)[2]) { print $uid . "\n" }'"'"' )' -- $cur ));
        else
            COMPREPLY=($( awk 'BEGIN {FS=":"} {if ($3 ~ /^'$cur'/) print $3}'        /etc/passwd ));
        fi;
    fi
}
_umount () 
{ 
    local cur IFS='
';
    COMPREPLY=();
    cur=`_get_cword`;
    local IFS='
';
    COMPREPLY=($( compgen -W '$( mount | cut -d" " -f 3 )' -- $cur ));
    return 0
}
_update_alternatives () 
{ 
    local cur prev mode args i;
    COMPREPLY=();
    cur=`_get_cword`;
    prev=${COMP_WORDS[COMP_CWORD-1]};
    case "$prev" in 
        --@(altdir|admindir))
            _filedir -d;
            return 0
        ;;
        --@(help|version))
            return 0
        ;;
    esac;
    for ((i=1; i < COMP_CWORD; i++ ))
    do
        if [[ "${COMP_WORDS[i]}" == --@(install|remove|auto|display|config|remove-all) ]]; then
            mode=${COMP_WORDS[i]};
            args=$(($COMP_CWORD - i));
            break;
        fi;
    done;
    case $mode in 
        --install)
            case $args in 
                1)
                    _filedir
                ;;
                2)
                    installed_alternatives
                ;;
                3)
                    _filedir
                ;;
            esac
        ;;
        --remove)
            case $args in 
                1)
                    installed_alternatives
                ;;
                2)
                    _filedir
                ;;
            esac
        ;;
        --auto)
            installed_alternatives
        ;;
        --remove-all)
            installed_alternatives
        ;;
        --display)
            installed_alternatives
        ;;
        --config)
            installed_alternatives
        ;;
        *)
            COMPREPLY=($( compgen -W '--verbose --quiet --help --version \
                   --altdir --admindir' -- $cur ) $( compgen -W '--install --remove --auto --display \
                   --config' -- $cur ))
        ;;
    esac
}
_update_rc_d () 
{ 
    local cur prev sysvdir services options valid_options;
    cur=`_get_cword`;
    prev=${COMP_WORDS[COMP_CWORD-1]};
    [ -d /etc/rc.d/init.d ] && sysvdir=/etc/rc.d/init.d || sysvdir=/etc/init.d;
    services=($(echo $sysvdir/!(README*|*.sh|*.dpkg*|*.rpm*)));
    services=(${services[@]#$sysvdir/});
    options=(-f -n);
    if [[ $COMP_CWORD -eq 1 || "$prev" == -* ]]; then
        valid_options=($(         echo "${COMP_WORDS[@]} ${options[@]}"         | tr " " "\n"         | sed -ne "/$( echo "${options[@]}" | sed "s/ /\\|/g" )/p"         | sort | uniq -u         ));
        COMPREPLY=($( compgen -W '${options[@]} ${services[@]}'         -X '$( echo ${COMP_WORDS[@]} | tr " " "|" )' -- $cur ));
    else
        if [[ "$prev" == ?($( echo ${services[@]} | tr " " "|" )) ]]; then
            COMPREPLY=($( compgen -W 'remove defaults start stop' -- $cur ));
        else
            if [[ "$prev" == defaults && "$cur" == [0-9] ]]; then
                COMPREPLY=(0 1 2 3 4 5 6 7 8 9);
            else
                if [[ "$prev" == defaults && "$cur" == [sk]?([0-9]) ]]; then
                    COMPREPLY=(0 1 2 3 4 5 6 7 8 9);
                else
                    if [[ "$prev" == defaults && -z "$cur" ]]; then
                        COMPREPLY=(0 1 2 3 4 5 6 7 8 9 s k);
                    else
                        if [[ "$prev" == ?(start|stop) ]]; then
                            if [[ "$cur" == [0-9] || -z "$cur" ]]; then
                                COMPREPLY=(0 1 2 3 4 5 6 7 8 9);
                            else
                                if [[ "$cur" == [0-9][0-9] ]]; then
                                    COMPREPLY=($cur);
                                else
                                    COMPREPLY=();
                                fi;
                            fi;
                        else
                            if [[ "$prev" == ?([0-9][0-9]|[0-6S]) ]]; then
                                if [[ -z "$cur" ]]; then
                                    if [[ $prev == [0-9][0-9] ]]; then
                                        COMPREPLY=(0 1 2 3 4 5 6 S);
                                    else
                                        COMPREPLY=(0 1 2 3 4 5 6 S .);
                                    fi;
                                else
                                    if [[ "$cur" == [0-6S.] ]]; then
                                        COMPREPLY=($cur);
                                    else
                                        COMPREPLY=();
                                    fi;
                                fi;
                            else
                                if [[ "$prev" == "." ]]; then
                                    COMPREPLY=($(compgen -W "start stop" -- $cur));
                                else
                                    COMPREPLY=();
                                fi;
                            fi;
                        fi;
                    fi;
                fi;
            fi;
        fi;
    fi;
    return 0
}
_user_at_host () 
{ 
    local cur;
    COMPREPLY=();
    cur=`_get_cword`;
    if [[ $cur == *@* ]]; then
        _known_hosts;
    else
        COMPREPLY=($( compgen -u -- "$cur" ));
    fi;
    return 0
}
_usergroup () 
{ 
    local IFS='
';
    cur=${cur//\\\\ / };
    if [[ $cur = *@(\\:|.)* ]] && [ -n "$bash205" ]; then
        user=${cur%%*([^:.])};
        COMPREPLY=($(compgen -P ${user/\\\\} -g -- ${cur##*[.:]}));
    else
        if [[ $cur = *:* ]] && [ -n "$bash205" ]; then
            COMPREPLY=($( compgen -g -- ${cur##*[.:]} ));
        else
            COMPREPLY=($( compgen -S : -u -- $cur ));
        fi;
    fi
}
_xrandr () 
{ 
    local cur prev output modes;
    COMPREPLY=();
    cur=`_get_cword`;
    prev=${COMP_WORDS[COMP_CWORD-1]};
    case "$prev" in 
        --output)
            local outputs=$(xrandr|grep 'connected'|awk '{print $1}');
            COMPREPLY=($(compgen -W "$outputs" -- $cur));
            return 0
        ;;
        --mode)
            for ((i = 1; i < COMP_CWORD; i++ ))
            do
                if [[ "${COMP_WORDS[i]}" == "--output" ]]; then
                    output=${COMP_WORDS[i+1]};
                    break;
                fi;
            done;
            modes=$(xrandr|sed -e "1,/$output/ d"             -e "/connected/,$ d"|awk '{print $1}');
            COMPREPLY=($( compgen -W "$modes" -- $cur));
            return 0
        ;;
    esac;
    case "$cur" in 
        *)
            COMPREPLY=($(compgen -W '-d -display -help -o \
                    --orientation -q --query -s --size\
                    -r --rate -v --version -x -y --screen \
                    --verbose --dryrun --prop --fb --fbmm --dpi \
                    --output --auto --mode --preferred --pos \
                    --reflect --rotate --left-of --right-of \
                    --above --below --same-as --set --off --crtc \
                    --newmode --rmmode --addmode --delmode' -- $cur));
            return 0
        ;;
    esac;
    return 0
}
command_not_found_handle () 
{ 
    if [ -x /usr/lib/command-not-found ]; then
        /usr/bin/python /usr/lib/command-not-found -- $1;
        return $?;
    else
        return 127;
    fi
}
dequote () 
{ 
    eval echo "$1"
}
installed_alternatives () 
{ 
    local admindir;
    for i in alternatives dpkg/alternatives rpm/alternatives;
    do
        [ -d /var/lib/$i ] && admindir=/var/lib/$i && break;
    done;
    for ((i=1; i < COMP_CWORD; i++ ))
    do
        if [[ "${COMP_WORDS[i]}" == --admindir ]]; then
            admindir=${COMP_WORDS[i+1]};
            break;
        fi;
    done;
    COMPREPLY=($( command ls $admindir | grep "^$cur" ))
}
quote () 
{ 
    echo \'${1//\'/\'\\\'\'}\'
}
quote_readline () 
{ 
    local t="${1//\\/\\\\}";
    echo \'${t//\'/\'\\\'\'}\'
}
ubuntu@ubuntu:~$ 
[/html]

---

### Post by lmarmisa on 2009-11-13
I did not tell you how prepare an Ubuntu 9.10 LiveCD. 

Simply download the ubuntu-9.10-desktop-i368.iso file from the link 

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

and burn a CD with it.

A second comment: sudo bash command will not ask for your password in this case because you are running a livecd version of Ubuntu.

I wish you that your nightmare finish very soon.

Best regards,

Luis

---

### Post by Kir_B on 2009-11-13
Thanks a million lmarmisa. I think I'm deciphering your instructions correctly, but to be safe I'd like to clarify whether or not your talking about the partition containing the Ubuntu OS? For me that would be "/dev/sda6", as you can see below. This is all the pertinent data from the partition editor:

Partition   File System   Label             Size       Flags
/dev/sda1   = Fat 16      = Dell Utility    47.03 MiB
/dev/sda2   = ntfs        = RECOVERY        10.00 GiB  Boot
/dev/sda3   = ntfs        = OS {Vista}      55.75 Gib
unallocated = unallocated                   70.07 GiB    
/dev/sda4   = extended    = linux partition 96.97 GiB
/dev/sda5   = linux swap  = linux-swap       1.86 GiB
/dev/sda6   = ext3        = Ubuntu          13.97 GiB
/dev/sda7   = ext3        = Home            81.13 GiB

Thanks again. Kirby

---

### Post by Kir_B on 2009-11-13
> **lmarmisa said:**
> I did not tell you how prepare an Ubuntu 9.10 LiveCD. 

Simply download the ubuntu-9.10-desktop-i368.iso file from the link 

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

and burn a CD with it.

A second comment: sudo bash command will not ask for your password in this case because you are running a livecd version of Ubuntu.

I wish you that your nightmare finish very soon.

Best regards,

Luis
I'm currently running off of a 9.04 live cd in safe graphics mode. I can't run the 9.10's for some reason. I just simply can't get more than the bottom right hand quarter of the screen in the upper left quarter of my monitor.

---

### Post by lmarmisa on 2009-11-13
Hi again, Kirby

Yes, I think that you are right. /dev/sda6 seems the correct partition.

I suppose that you have /dev/sda6 partition for the Ubuntu system and /dev/sda7 for the users' home.

Ubuntu 9.04 LiveCD seems quite good also.

Try to follow my instructions and good luck. If you have any doubt, don't hesitate to ask for help.

Best regards,

Luis

---

### Post by Kir_B on 2009-11-13
Thanks a lot Luis. I'm gonna give it a try right now!

---

### Post by lmarmisa on 2009-11-13
Taking into account the correct device /dev/sda6, these are the commands:

[B]sudo bash
mount /dev/sda6 /mnt
mount --bind /dev /mnt/dev
chroot /mnt
grub-install /dev/sda
update-grub[/B]

Any error during the process?

I would like that everything is fine.

Now, shutdown the computer (ubuntu -> shutdown) and remove the CD.

Grub should start correctly next time.

Regars,

Luis

---

### Post by Kir_B on 2009-11-13
ubuntu@ubuntu:~$ sudo bash
root@ubuntu:~# mount /dev/sda6 /mnt
root@ubuntu:~# mount --bind /dev mnt/dev
mount: mount point mnt/dev does not exist
root@ubuntu:~# 

This is what transpired. Did I do something wrong?

---

### Post by Kir_B on 2009-11-13
Sorry, my bad  "mount --bind /dev /mnt/dev" not "mount --bind /dev mnt/dev"

---

### Post by fluffman86 on 2009-11-14
ubuntu@ubuntu:~$ sudo bash
root@ubuntu:~# mkdir /mnt
root@ubuntu:~# mount /dev/sda6 /mnt
root@ubuntu:~# mount --bind /dev /mnt/dev

---

### Post by lmarmisa on 2009-11-14
Any problem with the other commands?

---

### Post by Kir_B on 2009-11-14
> **lmarmisa said:**
> Taking into account the correct device /dev/sda6, these are the commands:

[B]sudo bash
mount /dev/sda6 /mnt
mount --bind /dev /mnt/dev
chroot /mnt
grub-install /dev/sda
update-grub[/B]

Any error during the process?

I would like that everything is fine.

Now, shutdown the computer (ubuntu -> shutdown) and remove the CD.

Grub should start correctly next time.

Regars,

Luis

Below are the results of the commands, 

[html]ubuntu@ubuntu:~$ sudo bash
 root@ubuntu:~# mount /dev/sda6 /mnt
 root@ubuntu:~# mount --bind /dev mnt/dev
 mount: mount point mnt/dev does not exist
 root@ubuntu:~# mount --bind /dev /mnt/dev
 root@ubuntu:~# chroot /mnt
 root@ubuntu:/# grub-install /dev/sda
 Installation finished. No error reported.
 This is the contents of the device map /boot/grub/device.map.
 Check if this is correct or not. If any of the lines is incorrect,
 fix it and re-run the script `grub-install'.
 
 (fd0)    /dev/fd0
 (hd0)    /dev/sda
 root@ubuntu:/# update-grub
 Generating grub.cfg ...
 Found linux image: /boot/vmlinuz-2.6.31-14-generic
 Found initrd image: /boot/initrd.img-2.6.31-14-generic
 Found linux image: /boot/vmlinuz-2.6.28-16-generic
 Found initrd image: /boot/initrd.img-2.6.28-16-generic
 Found memtest86+ image: /boot/memtest86+.bin
 grep: /proc/mounts: No such file or directory
 Cannot find list of partitions!
 done
 root@ubuntu:/#[/html]Third from the bottom concerns me {Cannot find list of partitions!}, so I'll wait to reboot and hopefully get some more answers.??? Thanks a lot. Kirby

---

### Post by lmarmisa on 2009-11-14
Looks great, but you will have to add some lines to the /boot/grub/menu.lst in order be able to run your Windows Vista system.

I will explain it in my next post.

---

### Post by lmarmisa on 2009-11-14
Please, don't shut-down your system yet.

Now, try these commands:

[B]cd /boot/grub
gedit menu.lst
[/B]

Go to the end of file. The last lines will be similar to these:


[B]title        Ubuntu 9.04, memtest86+
uuid        896976ac-5080-4574-a557-964afb88ff06
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
[/B]

Please, append this new lines

[B]### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Microsoft Windows XP Professional
root        (hd0,2)
savedefault
makeactive
chainloader    +1
[/B]

With this change you will be able to select Windows Vista during the boot process.

---

### Post by Kir_B on 2009-11-14
This is the command is what caused all this:

   -rm -f /boot/grub/menu.lst*

These are the five pages that it removed. Each page 
separated by this: PAGE____________
                                ``````                                ````````````


[php]/boot/grub/menu.lst* {grub legacy}
```````````````````````````````````
___________________________________________________________
```````````````````````````````````````````````````````````
FIRSTPAGE/boot/grub/menu.lst_______________________________
```````````````````````````````````````````````````````````

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=bc6db48c-e366-4bf9-b061-e97404dcb1c7

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Chainload into GRUB 2
uuid            bc6db48c-e366-4bf9-b061-e97404dcb1c7
kernel          /boot/grub/core.img

title           ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
                
title           When you have verified GRUB 2 works, you can use this command to
root

title           complete the upgrade:  upgrade-from-grub-legacy
root

title           ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title           Ubuntu 9.10, kernel 2.6.31-14-generic
uuid            bc6db48c-e366-4bf9-b061-e97404dcb1c7
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro xforcevesa quiet splash
initrd          /boot/initrd.img-2.6.31-14-generic
quiet

title           Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid            bc6db48c-e366-4bf9-b061-e97404dcb1c7
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro xforcevesa single
initrd          /boot/initrd.img-2.6.31-14-generic

title           Ubuntu 9.10, kernel 2.6.28-16-generic
uuid            bc6db48c-e366-4bf9-b061-e97404dcb1c7
kernel          /boot/vmlinuz-2.6.28-16-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro xforcevesa quiet splash
initrd          /boot/initrd.img-2.6.28-16-generic
quiet

title           Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid            bc6db48c-e366-4bf9-b061-e97404dcb1c7
kernel          /boot/vmlinuz-2.6.28-16-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro xforcevesa single
initrd          /boot/initrd.img-2.6.28-16-generic

title           Ubuntu 9.10, memtest86+
uuid            bc6db48c-e366-4bf9-b061-e97404dcb1c7
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Dell Utility Partition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title           Windows Vista (loader)
rootnoverify    (hd0,2)
savedefault
makeactive
chainloader     +1

_____________________________________________________________
`````````````````````````````````````````````````````````````
SECONDPAGEboot/grub/menu.lst~________________________________
`````````````````````````````````````````````````````````````

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=bc6db48c-e366-4bf9-b061-e97404dcb1c7

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 9.10, kernel 2.6.31-14-generic
uuid            bc6db48c-e366-4bf9-b061-e97404dcb1c7
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro xforcevesa quiet splash 
initrd          /boot/initrd.img-2.6.31-14-generic
quiet

title           Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid            bc6db48c-e366-4bf9-b061-e97404dcb1c7
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro xforcevesa  single
initrd          /boot/initrd.img-2.6.31-14-generic

title           Ubuntu 9.10, kernel 2.6.28-16-generic
uuid            bc6db48c-e366-4bf9-b061-e97404dcb1c7
kernel          /boot/vmlinuz-2.6.28-16-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro xforcevesa quiet splash 
initrd          /boot/initrd.img-2.6.28-16-generic
quiet

title           Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid            bc6db48c-e366-4bf9-b061-e97404dcb1c7
kernel          /boot/vmlinuz-2.6.28-16-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro xforcevesa  single
initrd          /boot/initrd.img-2.6.28-16-generic

title           Ubuntu 9.10, memtest86+
uuid            bc6db48c-e366-4bf9-b061-e97404dcb1c7
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Dell Utility Partition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title           Windows Vista (loader)
rootnoverify    (hd0,2)
savedefault
makeactive
chainloader     +1

_____________________________________________________________
`````````````````````````````````````````````````````````````
THIRDPAGE/boot/grub/menu.lst.backup__________________________
`````````````````````````````````````````````````````````````
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=bc6db48c-e366-4bf9-b061-e97404dcb1c7

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 9.10, kernel 2.6.31-14-generic
uuid            bc6db48c-e366-4bf9-b061-e97404dcb1c7
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro xforcevesa quiet splash 
initrd          /boot/initrd.img-2.6.31-14-generic
quiet

title           Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid            bc6db48c-e366-4bf9-b061-e97404dcb1c7
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro xforcevesa  single
initrd          /boot/initrd.img-2.6.31-14-generic

title           Ubuntu 9.10, kernel 2.6.28-16-generic
uuid            bc6db48c-e366-4bf9-b061-e97404dcb1c7
kernel          /boot/vmlinuz-2.6.28-16-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro xforcevesa quiet splash 
initrd          /boot/initrd.img-2.6.28-16-generic
quiet

title           Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid            bc6db48c-e366-4bf9-b061-e97404dcb1c7
kernel          /boot/vmlinuz-2.6.28-16-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro xforcevesa  single
initrd          /boot/initrd.img-2.6.28-16-generic

title           Ubuntu 9.10, memtest86+
uuid            bc6db48c-e366-4bf9-b061-e97404dcb1c7
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Dell Utility Partition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title           Windows Vista (loader)
rootnoverify    (hd0,2)
savedefault
makeactive
chainloader     +1

_____________________________________________________________
`````````````````````````````````````````````````````````````
FOURTHPAGE/boot/grub/menu.lst_backup_by_grub2_postinst_______
`````````````````````````````````````````````````````````````
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=bc6db48c-e366-4bf9-b061-e97404dcb1c7

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 9.10, kernel 2.6.31-14-generic
uuid            bc6db48c-e366-4bf9-b061-e97404dcb1c7
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro xforcevesa quiet splash 
initrd          /boot/initrd.img-2.6.31-14-generic
quiet

title           Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid            bc6db48c-e366-4bf9-b061-e97404dcb1c7
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro xforcevesa  single
initrd          /boot/initrd.img-2.6.31-14-generic

title           Ubuntu 9.10, kernel 2.6.28-16-generic
uuid            bc6db48c-e366-4bf9-b061-e97404dcb1c7
kernel          /boot/vmlinuz-2.6.28-16-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro xforcevesa quiet splash 
initrd          /boot/initrd.img-2.6.28-16-generic
quiet

title           Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid            bc6db48c-e366-4bf9-b061-e97404dcb1c7
kernel          /boot/vmlinuz-2.6.28-16-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro xforcevesa  single
initrd          /boot/initrd.img-2.6.28-16-generic

title           Ubuntu 9.10, memtest86+
uuid            bc6db48c-e366-4bf9-b061-e97404dcb1c7
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Dell Utility Partition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title           Windows Vista (loader)
rootnoverify    (hd0,2)
savedefault
makeactive
chainloader     +1

____________________________________________________________
````````````````````````````````````````````````````````````
FIFTHPAGE/boot/grub/menu.lst.original_______________________
````````````````````````````````````````````````````````````
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=bc6db48c-e366-4bf9-b061-e97404dcb1c7

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Chainload into GRUB 2
uuid            bc6db48c-e366-4bf9-b061-e97404dcb1c7
kernel          /boot/grub/core.img

title           ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
                
title           When you have verified GRUB 2 works, you can use this command to
root

title           complete the upgrade:  upgrade-from-grub-legacy
root

title           ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title           Ubuntu 9.10, kernel 2.6.31-14-generic
uuid            bc6db48c-e366-4bf9-b061-e97404dcb1c7
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro xforcevesa quiet splash
initrd          /boot/initrd.img-2.6.31-14-generic
quiet

title           Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid            bc6db48c-e366-4bf9-b061-e97404dcb1c7
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro xforcevesa single
initrd          /boot/initrd.img-2.6.31-14-generic

title           Ubuntu 9.10, kernel 2.6.28-16-generic
uuid            bc6db48c-e366-4bf9-b061-e97404dcb1c7
kernel          /boot/vmlinuz-2.6.28-16-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro xforcevesa quiet splash
initrd          /boot/initrd.img-2.6.28-16-generic
quiet

title           Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid            bc6db48c-e366-4bf9-b061-e97404dcb1c7
kernel          /boot/vmlinuz-2.6.28-16-generic root=UUID=bc6db48c-e366-4bf9-b061-e97404dcb1c7 ro xforcevesa single
initrd          /boot/initrd.img-2.6.28-16-generic

title           Ubuntu 9.10, memtest86+
uuid            bc6db48c-e366-4bf9-b061-e97404dcb1c7
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Dell Utility Partition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title           Windows Vista (loader)
rootnoverify    (hd0,2)
savedefault
makeactive
chainloader     +1[/php]

---

### Post by lmarmisa on 2009-11-14
If you have to write by hand the new lines, don't copy comments (lines starting with #).

The important info is

[B]title        Other operating systems:
root

[/B][B]title        Microsoft Windows Vista
root        (hd0,2)
savedefault
makeactive
chainloader    +1[/B]

---

### Post by lmarmisa on 2009-11-14
/boot/grub/menu.lst is a very importan file if you use grub.

---

### Post by Kir_B on 2009-11-14
This is the result:

root@ubuntu:/# cd boot/grub
root@ubuntu:/boot/grub# gedit menu.lst
No protocol specified

(gedit:14896): Gtk-WARNING **: cannot open display: :0.0
root@ubuntu:/boot/grub# 


Ouch!!!

---

### Post by lmarmisa on 2009-11-14
Hmmm. I see some problems now. I have checked teh result of the commands and it seems that you are running grub2, not grub.
The result says generating grub.cfg -> you have grub2 and menu.lst is not used in this case.
[B]
Generating grub.cfg ...[/B]

My doubt is why Vista perating system is not recognized.

Could you write the command

**update-grub2**

Sorry by my mistake about grub.

---

### Post by lmarmisa on 2009-11-14
Let me ask a question.

Do you continue running LiveCD?

If the answer is yes, try to write the command

**update-grub2**

in the terminal where you wrote the grub-install command.

---

### Post by Kir_B on 2009-11-14
Here's the results:

root@ubuntu:/boot/grub# update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
Found memtest86+ image: /boot/memtest86+.bin
grep: /proc/mounts: No such file or directory
Cannot find list of partitions!
done
root@ubuntu:/boot/grub# 

    Thanks again. Kirby

---

### Post by lmarmisa on 2009-11-14
The result of update-grub2 is not too bad, but I don't understand why it is not able to find your Vista partition.

Apparently, grub2 will be able to start Ubuntu next time, but no Vista.

---

### Post by lmarmisa on 2009-11-14
Ok. I recommend you shutdown now, remove the cd and restart.

We will see if the Ubuntu start normally.

---

### Post by Kir_B on 2009-11-14
Vista is still there and untouched. Will grub2 recognise it when it's operational?

I'll wait for a reply and then attempt a reboot

                 Thanks a million. Kirby

---

### Post by lmarmisa on 2009-11-14
Yes. Vista is not touched and it is operational, but grub2 is unable lo select it at the moment. Grub change the first bytes  of the Master Boot Record (MBR) and takes the role of the Vista loader. So, we have to repair grub in order to star Vista.

---

### Post by Kir_B on 2009-11-14
So rebooting right now would be wise???

---

### Post by lmarmisa on 2009-11-14
Yes. We will see if Ubuntu start correctly.

---

### Post by lmarmisa on 2009-11-14
I have change my user's profile in such a way that other users are able to send me private messages. May be you could send me one of this messages with your email address. I am not sure if we will need some time in order to solve your problem.

---

### Post by Kir_B on 2009-11-14
My terminal tells me that there is still a process running when I try to close it. Should I close it anyhow?

---

### Post by Kir_B on 2009-11-14
> **Kir_B said:**
> My terminal tells me that there is still a process running when I try to close it. Should I close it anyhow?
The answer to that question {via email}, was yes, force it if you have to. I just let the computer deal with it and selected "Restart". It booted up with all my normal Ubuntu options on what would normally appear after the "Chainload into grub2 screen". No more Chainloader screen and No Vista option, but it does now boot into Ubuntu. You never know how nice something is until it's gone!!! I love my desktop, and it's even nicer after being restricted to the Jaunty Livecd desktop

---

### Post by Kir_B on 2009-11-14
The following is what Luis had me do next:

First, this command in the terminal, followed by my password:
sudo update-grub2

The following are the results displayed in the terminal:
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Dell Utility Partition on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
Found Windows Vista (loader) on /dev/sda3
done

I sent Luis an email of these results, to which he responded with a 100% guarantee that we were successful and had me reboot into Vista. I followed his command and he was 100% correct. Vista loads quicker than Ubuntu, but essentially, Problem solved. Praise LUIS. Thank you Luis. 

And thank everyone else that looked into this problem for me. Without you all I'd be resigned to using the Microsoft Spy System!!! What a waste of resources it is to compile data on everyone of us. 

                \\:D/   THANKS AGAIN. Kirby  \\:D/

P.S. anyone looking to customize their firefox, might want look at 
[COLOR=#00cccc][COLOR=#000000][My Firefox add-on collection. Karmic]("https://addons.mozilla.org/en-US/firefox/collection/karmic")[/COLOR][/COLOR]. Take a scroll through the list and you might find something you'll one day wonder how you lived without. Peace everyone.

---

### Post by JasonSilver on 2010-02-08
> **lmarmisa said:**
> Hello Kirby,

the upgrade from 9.04 to 9.10 does not change the grub version. Grub2 is installed only in new installations.

I would recommend you to re-install your grub program.

Start your computer from a Ubuntu 9.10 LiveCD and select Try Ubuntu without any change to your computer.

When the start is finshed, open Gparted (System -> Administration -> GParted) and try to locate the Ubuntu partition (probably a File System ext3 or ext4). I will suppose that this partitios is /dev/sda1. If no, please, chage it with the correct device. 

Open a terminal (Applications -> Accessories -> Terminal)

Type the following commands:

sudo bash                     #the system will ask for your password
mount /dev/sda1 /mnt   #May be your device is not /dev/sda1
mount --bind /dev /mnt/dev
chroot /mnt
grub-install /dev/sda     #no number here
update-grub

I hope that you does not get any error on these commands.

That is all.

And now, cross your fingers, shutdown your computer, extract the CD and boot your system again.

The system should be start normally with the new grub loader.

Best regards,

Luis
This didn't work for me-- I have tried all kinds of combinations of (hdX,X) and keep getting partitition not found.

Can I say now that I hate this? Is this all grub2's fault? I have three or four kernels it seems and only one of them boots. What's with that?

VERY furstrated.

---

