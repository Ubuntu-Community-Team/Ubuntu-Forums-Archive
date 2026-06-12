---
title: "bash script logging"
date: 2011-03-10
forum: General Help
---

### Post by kios on 2011-03-10
Hy
I have a bash script that i created for a colleague to configure the servers he installs.  It does package installations, modifies some config files, creates directories... 
The problem is sometimes he says that the script skips some steps. There are some steps that require user input and i think he chooses wrong option. (i have tested the script and it works fine).

My question is how can i save the output in a file (or log) so i can check if there are error? I know about the ">>" operators but will this "script.sh >> output.txt" still bring the dialogs for user input (like read input from shell and mysql password dialog from install package)? And how can i record everything he inputs?

I read about logger, but since there are a lot of commands do i have to log every command or can i just log the whole script.

Thanks.

---

### Post by MaxIBoy on 2011-03-10
Logger really isn't the right tool for the job. It logs everything to the operating system logs and is only appropriate for scripts used during the boot sequence and things like that.

The magic tool here is the "tee" command, which writes its input to a file *and* echoes it out on stdout, allowing for pipes resembling a sort of T-junction.

My first guess would be to do something like this:
```
cat - | tee -a output.txt | ./script.sh | tee -a output.txt
```Note- if the log file already exists, new content will just be added to the end of it. I suspect this might garble the output in unpredictable ways if, for example, your user is typing input at the same time as the script is echoing output. 

I'm going to edit this post and add a "safer" solution, hold on.

EDIT: Okay, here's a version which guarantees no garbling, by date stamping each line and keeping input and output in separate files. This is WAY OVER-ENGINEERED for most cases, and unless the log itself is really critical (and not just a throwaway debug tool) then the above solution is probably better-- so if you found this forum post through Google, take note. Also, this solution requires process substitution, which is Bash-only and won't work on other shells. 
```
function date_filter {
    while read line ; do
            echo "`date +%s%N`:$line"; done; 
}
cat - | tee >( date_filter >> /tmp/input_log ) | bash | tee >( date_filter >> /tmp/output_log )
cat /tmp/input_log /tmp/output_log | sort | sed "s/^[0-9]*://1" > final_log
```**EDIT again** If you want to capture error messages, you need to redirect stderr as well as/instead of stdout, so you'll need to adjust my suggestions accordingly. 
```
./script.sh >> logfile #does not capture error messages, only "normal" messages
./script.sh 2>&1 >> logfile #captures  both; the 2>&1 redirects stderr to stdout. 
./script.sh 2>>logfile #captures only error messages, "normal" messages go their merry way.
```

---

### Post by kios on 2011-03-11
thanks for the reply. will try this today because i really need it. i don't have time to check all the server's configuration every time.  

One question only. The log function needs to be called before everything else right?

---

### Post by kios on 2011-03-11
hey... i tried the function but i don't think it's working. for starters i have encapsulated all command in the function's while/do loop, but there is no console output. it does create the two log files but i cant tell if it requires user input or not. 
here is some sample code from the script i'm using:

```

    logDir="~/logs"
    if [ ! -d "$logDir" ]; then
    sudo mkdir logs;
    echo "Logging directory created";
    else
    echo "Directory already exists";
    fi
    ##################################
    #Backing-up original files       #
    ##################################
    echo
    echo
    echo "Copying original files to ~/backup in case of failure"
    echo "Run replace.sh if something goes wrong"
    echo
    echo
    backupDir="~/backup"
    if [ ! -d "$backupDir" ]; then
    sudo mkdir backup;
    echo "Backup directory created";
    else
    echo "Directory already exists";
    fi
    sudo cp -rp /etc/sudoers ~/backup
    sudo cp -rp /etc/hosts ~/backup
    sudo cp -rp /etc/network/interfaces ~/backup
    sudo cp -rp /etc/apt/sources.list ~/backup
    sudo cp -rp /etc/nsswitch.conf ~/backup
    echo "Original files copied"

    serverVersion=""
    ##################################
    #Choose Ubuntu server version    #
    ##################################
    echo
    while :
    do
    echo "PLEASE CHOOSE SERVER VERSION"
    echo "1. Ubuntu Server 10.10"
    echo "2. Ubuntu Server 10.04"
    echo -n "Insert option: "
    read optiuneServer
    case $optiuneServer in
      1) serverVersion="maverick";
	break;;
      2) serverVersion="lucid";
	break;;
      *) echo "Wrong choice";;
    esac
    done
    echo
     ##################################
    #Modyfing sources.list for apt   #
    #to include partner packages     #
    ##################################
    echo "Including partner packages in sources.list"
    if [ "$serverVersion" = "lucid" ]; then
    sudo sed -ie 's|# deb http://archive.canonical.com/ubuntu lucid partner|deb http://archive.canonical.com/ubuntu lucid partner|g' /etc/apt/sources.list
    sudo sed -ie 's|# deb-src http://archive.canonical.com/ubuntu lucid partner|deb-src http://archive.canonical.com/ubuntu lucid partner|g' /etc/apt/sources.list
    elif [ "$serverVersion" = "maverick" ]; then
    sudo sed -ie 's|# deb http://archive.canonical.com/ubuntu maverick partner|deb http://archive.canonical.com/ubuntu maverick partner|g' /etc/apt/sources.list
    sudo sed -ie 's|# deb-src http://archive.canonical.com/ubuntu maverick partner|deb-src http://archive.canonical.com/ubuntu maverick partner|g' /etc/apt/sources.list
    fi
    echo "Updating sources for aptitude"
    sudo aptitude update
    echo
    ##################################
    #Modyfing /etc/sudoers file      #
    #to include allowed commands     #
    ##################################
    echo "Modifying /etc/sudoers as required"
    sudo sed -ie 's|# Cmnd alias specification|# Cmnd alias specification\nCmnd_Alias COMMANDS_NEEDED=/bin/chmod, /bin/chown|g' /etc/sudoers
    sudo sed -ie 's|%admin ALL=(ALL) ALL|%admin ALL=(ALL) ALL\nuser ALL=(ALL) NOPASSWD: COMMANDS_NEEDED|g' /etc/sudoers
    echo
    ##################################
    #Installing default list of      #
    #packages			 #
    ##################################
    echo "Downloading package list"
    scp user@255.255.255.555:/home/user/package_list /home/user/
    echo "Setting package list to install"
    sudo dpkg --set-selections < /home/user/package_list
    echo "Installing dselect for automatic install"
    sudo apt-get install dselect -y
    echo "Installing packages. This may take a while"
    echo "Waiting 10 seconds so you can read this"
    sleep 10
    sudo dselect install
    echo "Finished installing packages (hopefully with no errors)"
    echo

```

as you can see there are some commands that require user input (case selections or package installation dialogs). and if don't have any output on screen i can't use it.
thanks

---

