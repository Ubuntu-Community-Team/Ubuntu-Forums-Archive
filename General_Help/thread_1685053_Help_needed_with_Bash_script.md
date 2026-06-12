---
title: "Help needed with Bash script"
date: 2011-02-10
forum: General Help
---

### Post by Barry Cent on 2011-02-10
Hi,

Would anyone happen to be able to tell me why I'm receiving the following result from this script?

My script:
```
joe@Server:~$ cat .backup-scripts/offsite-transfer.sh
#!/bin/bash
# Offsite Backup Transfer Script

SERVERBACKUPLOCAL=/mnt/usb_backup/Backups/Server
SERVERBACKUPREMOTE=/mnt/mac_backup/Server

TOOLSBACKUPLOCAL=/mnt/usb_backup/Backups/Tools
TOOLSBACKUPREMOTE=/mnt/mac_backup/Tools

SVNBACKUPLOCAL=/mnt/usb_backup/Backups/SVN
SVNBACKUPREMOTE=/mnt/mac_backup/SVN

EMAILBACKUPLOCAL=/mnt/usb_backup/Backups/Email/MobileMe
EMAILBACKUPREMOTE=/mnt/mac_backup/Email/MobileMe

if [ -f $SERVERBACKUPLOCAL/server-backup.log ]; then
rm -rf $SERVERBACKUPREMOTE/*
cp -v $SERVERBACKUPLOCAL/* $SERVERBACKUPREMOTE > $SERVERBACKUPREMOTE/server-backup-transfer.log
        elif [ -f $SERVERBACKUPREMOTE/server-backup.log ]; then
        rm -rf $SERVERBACKUPLOCAL/*
fi
fi

if [ -f $TOOLSBACKUPLOCAL/tools-usb-backup.log ]; then
rm -rf $TOOLSBACKUPREMOTE/*
cp -v $TOOLSBACKUPLOCAL/* $TOOLSBACKUPREMOTE > $TOOLSBACKUPREMOTE/tools-usb-backup-transfer.log
        if [ -f $TOOLSBACKUPREMOTE/tools-usb-backup.log ]; then
        rm -rf $TOOLSBACKUPLOCAL/*
        fi
fi

if [ -f $SVNBACKUPLOCAL/svn-backup.log ]; then
rm -rf $SVNBACKUPREMOTE/*
cp -v $SVNBACKUPLOCAL/* $SVNBACKUPREMOTE > $SVNBACKUPREMOTE/svn-backup-transfer.log
        if [ -f $SVNBACKUPREMOTE/svn-backup.log ]; then
        rm -rf $SVNBACKUPLOCAL/*
        fi
fi

if [ -f /var/log/email-backup/MobileMe_Deleted_Messages.log ]; then
rm -rf $EMAILBACKUPREMOTE/*
cp -v $EMAILBACKUPLOCAL/* $EMAILBACKUPREMOTE > $EMAILBACKUPREMOTE/email-backup-transfer.log
        if [ -f $EMAILBACKUPREMOTE/email-backup-transfer.log ]; then
        rm -rf $EMAILBACKUPLOCAL/*
        fi
fi

if [ -f $SERVERBACKUPREMOTE/server-backup.log ]; then
        if [ -f $TOOLSBACKUPREMOTE/tools-usb-backup.log ]; then
                if [ -f $SVNBACKUPREMOTE/svn-backup.log ]; then
                        if [ -f $EMAILBACKUPREMOTE/email-backup-transfer.log ]; then
                                echo "______________________________________________________________________________________________________________________" >> /tmp/overnight-jobs.log
                                echo "" >> /tmp/overnight-jobs.log
                                echo "The offsite transfer of backup files from your server to your iMac completed successfully last night." >> /tmp/overnight-jobs.log
                                echo "" >> /tmp/overnight-jobs.log
                                echo "" >> /tmp/overnight-jobs.log
                                echo "" >> /tmp/overnight-jobs.log

                        else
                                echo "______________________________________________________________________________________________________________________" >> /tmp/overnight-jobs.log
                                echo "" >> /tmp/overnight-jobs.log
                                echo "At least one set of backup files failed to transfer last night from your server to your iMac." >> /tmp/overnight-jobs.log
                                echo "" >> /tmp/overnight-jobs.log
                                echo "Please view one of the following log files for more information why this job did not compelte successfully..." >> /tmp/overnight-jobs.log
                                echo "" >> /tmp/overnight-jobs.log
                                tail $SERVERBACKUPREMOTE/server-backup-transfer.log >> /tmp/overnight-jobs.log
                                echo "" >> /tmp/overnight-jobs.log
                                tail $TOOLSBACKUPREMOTE/server-backup-transfer.log >> /tmp/overnight-jobs.log
                                echo "" >> /tmp/overnight-jobs.log
                                tail $SVNBACKUPREMOTE/svn-backup-transfer.log >> /tmp/overnight-jobs.log
                                echo "" >> /tmp/overnight-jobs.log
                                tail $EMAILBACKUPREMOTE/email-backup-transfer.log >> /tmp/overnight-jobs.log
                                echo "" >> /tmp/overnight-jobs.log
                                echo "" >> /tmp/overnight-jobs.log
                                echo "" >> /tmp/overnight-jobs.log
                        fi
                else
                        echo "______________________________________________________________________________________________________________________" >> /tmp/overnight-jobs.log
                        echo "" >> /tmp/overnight-jobs.log
                        echo "At least one set of backup files failed to transfer last night from your server to your iMac." >> /tmp/overnight-jobs.log
                        echo "" >> /tmp/overnight-jobs.log
                        echo "Please view on of the following log files for more information why this job did not compelte successfully..." >> /tmp/overnight-jobs.log
                        echo "" >> /tmp/overnight-jobs.log
                        tail $SERVERBACKUPREMOTE/server-backup-transfer.log >> /tmp/overnight-jobs.log
                        echo "" >> /tmp/overnight-jobs.log
                        tail $SERVERBACKUPREMOTE/server-backup-transfer.log >> /tmp/overnight-jobs.log
                        echo "" >> /tmp/overnight-jobs.log
                        tail $SVNBACKUPREMOTE/svn-backup-transfer.log >> /tmp/overnight-jobs.log
                        echo "" >> /tmp/overnight-jobs.log
                        tail $EMAILBACKUPREMOTE/email-backup-transfer.log >> /tmp/overnight-jobs.log
                        echo "" >> /tmp/overnight-jobs.log
                        echo "" >> /tmp/overnight-jobs.log
                        echo "" >> /tmp/overnight-jobs.log
                fi
        else
                echo "______________________________________________________________________________________________________________________" >> /tmp/overnight-jobs.log
                echo "" >> /tmp/overnight-jobs.log
                echo "At least one set of backup files failed to transfer last night from your server to your iMac." >> /tmp/overnight-jobs.log
                echo "" >> /tmp/overnight-jobs.log
                echo "Please view on of the following log files for more information why this job did not compelte successfully..." >> /tmp/overnight-jobs.log
                echo "" >> /tmp/overnight-jobs.log
                tail $SERVERBACKUPREMOTE/server-backup-transfer.log >> /tmp/overnight-jobs.log
                echo "" >> /tmp/overnight-jobs.log
                tail $SERVERBACKUPREMOTE/server-backup-transfer.log >> /tmp/overnight-jobs.log
                echo "" >> /tmp/overnight-jobs.log
                tail $SVNBACKUPREMOTE/svn-backup-transfer.log >> /tmp/overnight-jobs.log
                echo "" >> /tmp/overnight-jobs.log
                tail $EMAILBACKUPREMOTE/email-backup-transfer.log >> /tmp/overnight-jobs.log   
                echo "" >> /tmp/overnight-jobs.log
                echo "" >> /tmp/overnight-jobs.log
                echo "" >> /tmp/overnight-jobs.log
        fi
else
        echo "______________________________________________________________________________________________________________________" >> /tmp/overnight-jobs.log
        echo "" >> /tmp/overnight-jobs.log
        echo "At least one set of backup files failed to transfer last night from your server to your iMac." >> /tmp/overnight-jobs.log
        echo "" >> /tmp/overnight-jobs.log
        echo "Please view on of the following log files for more information why this job did not compelte successfully..." >> /tmp/overnight-jobs.log
        echo "" >> /tmp/overnight-jobs.log
        tail $SERVERBACKUPREMOTE/server-backup-transfer.log >> /tmp/overnight-jobs.log
        echo "" >> /tmp/overnight-jobs.log
        tail $SERVERBACKUPREMOTE/server-backup-transfer.log >> /tmp/overnight-jobs.log
        echo "" >> /tmp/overnight-jobs.log
        tail $SVNBACKUPREMOTE/svn-backup-transfer.log >> /tmp/overnight-jobs.log
        echo "" >> /tmp/overnight-jobs.log
        tail $EMAILBACKUPREMOTE/email-backup-transfer.log >> /tmp/overnight-jobs.log
        echo "" >> /tmp/overnight-jobs.log
        echo "" >> /tmp/overnight-jobs.log
        echo "" >> /tmp/overnight-jobs.log
fi

```


Output from running script:
```
.backup-scripts/offsite-transfer.sh: line 22: syntax error near unexpected token `fi'
.backup-scripts/offsite-transfer.sh: line 22: `fi'

```

I can't seem to work out what it's complaining about.

Best regards,

Joe

---

### Post by DaithiF on 2011-02-10
you have **fi **appearing twice at lines 21/22 -- delete one of them

---

### Post by Barry Cent on 2011-02-10
> **DaithiF said:**
> you have **fi **appearing twice at lines 21/22 -- delete one of them
The reason for this is because I am closing off the two if statements above. Surely, without the second fi, the statement will not be closed?

Thank you very much for your input!

Joe

---

### Post by DaithiF on 2011-02-10
I only see one if statement, not two.

```
**if** [ -f $SERVERBACKUPLOCAL/server-backup.log ]; then
rm -rf $SERVERBACKUPREMOTE/*
cp -v $SERVERBACKUPLOCAL/* $SERVERBACKUPREMOTE > $SERVERBACKUPREMOTE/server-backup-transfer.log
        elif [ -f $SERVERBACKUPREMOTE/server-backup.log ]; then
        rm -rf $SERVERBACKUPLOCAL/*
fi
fi

```

elif doesn't count as a new if -- its part of the same if / elif / fi block, requiring just one closing fi

---

### Post by Barry Cent on 2011-02-10
So it is. Complete lack of knowledge there! (on my behalf)

Thank you so much for your help. 

Joe

---

### Post by Dimitris1989 on 2011-03-15
hi, i am beginner in bash script and i have the following code


#!/bin/bash

#Declare string S1
#Declare string S2

S1="phone"
S2="new"
flag1=0
flag2=0

touch phonelist.txt

while [ $flag2 -eq 0 ] ; do

	echo "If you want to continue press 0, else press 1"
	read $flag2

	if [ $flag2 -eq 1 ] ; then
		break
	else

		read -e word1 word2 word3 word4 word5

		if [ $S1 = $word1 ] ; then

			if [ $S2 = $word2 ] ; then 
        	
 					echo -e $word3 $word4 $word5\n > phonelist
			else	

					for WORD in `cat phonelist`
					do

			 			if [ $flag1 -eq 2 ] ; then
                                        		echo $WORD
                                        		break

						else	
							if [ $flag1 -eq 0 ] ; then
         				
								if [ $WORD = $word2 ] ; then
             								flag1=1
								else
									flag1=0
								fi
				
							else

								if [ $WORD = $word3 ] ; then
									flag1=2
								else
									flag1=0
								fi
							fi
						fi
					done
		else 

  			echo "Incorrect command"

		fi

	fi

done


When i compile it with the command "chmod +x phone",(phone is the name of my file) and with the command "./phone" i get the following result:

./phone: line 57: syntax error near unexpected token `else'
./phone: line 57: `		else '


Could anyone please tell me with a quick glance where is the syntax error?Thank you

---

### Post by Dimitris1989 on 2011-03-15
i rewrote it in order to be more understandabe(sorry about that!)
hi, i am beginner in bash script and i have the following code


#!/bin/bash

#Declare string S1
#Declare string S2

S1="phone"
S2="new"
flag1=0
flag2=0

touch phonelist.txt

while [ $flag2 -eq 0 ] ; do

echo "If you want to continue press 0, else press 1"
read $flag2

if [ $flag2 -eq 1 ] ; then
   break
   else

   read -e word1 word2 word3 word4 word5

   if [ $S1 = $word1 ] ; then

      if [ $S2 = $word2 ] ; then 

         echo -e $word3 $word4 $word5\n > phonelist
      else	

         for WORD in `cat phonelist`
         do

         if [ $flag1 -eq 2 ] ; then
         echo $WORD
         break

         else	
         if [ $flag1 -eq 0 ] ; then

             if [ $WORD = $word2 ] ; then
                  flag1=1
             else
                  flag1=0
             fi

        else

             if [ $WORD = $word3 ] ; then
                  flag1=2
             else
                 flag1=0
             fi
        fi
       fi

       done
else 

echo "Incorrect command"

fi

fi

done


When i compile it with the command "chmod +x phone",(phone is the name of my file) and with the command "./phone" i get the following result:

./phone: line 57: syntax error near unexpected token `else'
./phone: line 57: `	 else '


Could anyone please tell me with a quick glance where is the syntax error?Thank you

---

### Post by Krytarik on 2011-03-16
@Dimitris1989: I stopped trying to close the if/else/fi statements, because it is simply to hard to read, sorry. Please enclose the code the next time in code-tags (the #-button in the editor), it should be much better to read then.

Greetings.

---

### Post by Dimitris1989 on 2011-03-16
i hope this is more helpful!


```

```#!/bin/bash

#Declare string S1```

#Declare string S2

S1="phone"
S2="new"
flag1=0
flag2=0

touch phonelist.txt

while [ $flag2 -eq 0 ] ; do

echo "If you want to continue press 0, else press 1"
read $flag2

if [ $flag2 -eq 1 ] ; then
    break
else

    read -e word1 word2 word3 word4 word5

    if [ $S1 = $word1 ] ; then

          if [ $S2 = $word2 ] ; then 

               echo -e $word3 $word4 $word5\n > phonelist
          else	

              for WORD in `cat phonelist`
              do

              if [ $flag1 -eq 2 ] ; then
                 echo $WORD
                 break

              else	
                 if [ $flag1 -eq 0 ] ; then

                     if [ $WORD = $word2 ] ; then
                          flag1=1
                     else
                          flag1=0
                      fi

                 else

                      if [ $WORD = $word3 ] ; then
                          flag1=2
                      else
                          flag1=0
                     fi
                fi
            fi

            done
     else 

        echo "Incorrect command"

     fi

fi

done


When i compile it with the command "chmod +x phone",(phone is the name of my file) and with the command "./phone" i get the following result:

./phone: line 57: syntax error near unexpected token `else'
./phone: line 57: `	 else '[CODE]
```

---

### Post by Dimitris1989 on 2011-03-16
```

```
#!/bin/bash

#Declare string S1[CODE]
#Declare string S2

S1="phone"
S2="new"
flag1=0
flag2=0

touch phonelist.txt

while [ $flag2 -eq 0 ] ; do

echo "If you want to continue press 0, else press 1"
read $flag2

if [ $flag2 -eq 1 ] ; then
  break
else

 read -e word1 word2 word3 word4 word5

  if [ $S1 = $word1 ] ; then

   if [ $S2 = $word2 ] ; then 

   echo -e $word3 $word4 $word5\n > phonelist
     else	

      for WORD in `cat phonelist`
       do

       if [ $flag1 -eq 2 ] ; then
         echo $WORD
         break

       else	
           if [ $flag1 -eq 0 ] ; then

               if [ $WORD = $word2 ] ; then
                 flag1=1
               else
                 flag1=0
               fi

           else

              if [ $WORD = $word3 ] ; then
                   flag1=2
               else
                  flag1=0
               fi
            fi
         fi

     done
     else 

     echo "Incorrect command"

   fi

fi

done

---

### Post by Dimitris1989 on 2011-03-16
Sorry,but can someone please guide me how to tag my code,like Barry Cent so as to show it in an readable way?Thank you...

---

### Post by Krytarik on 2011-03-16
> **Dimitris1989 said:**
> Sorry,but can someone please guide me how to tag my code,like Barry Cent so as to show it in an readable way?Thank you...
- paste the code of your script into the editor
- mark the code
- press the #-button at the right-upper of the editor

You may edit the first or last of your posts in that way (advanced mode), and then edit the excess posts and replace them with just a "." to make the thread more readable.

---

### Post by Dimitris1989 on 2011-03-16
#!/bin/bash

#Declare string S1[CODE]
#Declare string S2

S1="phone"
S2="new"
flag1=0
flag2=0

touch phonelist.txt

while [ $flag2 -eq 0 ] ; do

echo "If you want to continue press 0, else press 1"
read $flag2

if [ $flag2 -eq 1 ] ; then
--break
else

--read -e word1 word2 word3 word4 word5

---if [ $S1 = $word1 ] ; then

------if [ $S2 = $word2 ] ; then 

---------echo -e $word3 $word4 $word5\n > phonelist
------else	

---------for WORD in `cat phonelist`
---------do

---------if [ $flag1 -eq 2 ] ; then
------------echo $WORD
------------break

---------else	
------------if [ $flag1 -eq 0 ] ; then

---------------if [ $WORD = $word2 ] ; then
------------------flag1=1
---------------else
------------------flag1=0
---------------fi

------------else

---------------if [ $WORD = $word3 ] ; then
------------------flag1=2
---------------else
------------------flag1=0
---------------fi
------------fi
---------fi

---------done
---else 

-------echo "Incorrect command"

---fi

fi

done

i hope this works better

---

### Post by matt_symes on 2011-03-16
Hi

Still did not work. 

Highlight the text you want to put in code tags.
Hit the # button

or you can just surrond you text with the tags

[code] [/code}

Where the last tag is a square bracket.

Kind regards

---

### Post by Dimitris1989 on 2011-03-16
```
#!/bin/bash

#Declare string S1[CODE]
#Declare string S2

S1="phone"
S2="new"
flag1=0
flag2=0

touch phonelist.txt

while [ $flag2 -eq 0 ] ; do

echo "If you want to continue press 0, else press 1"
read $flag2

if [ $flag2 -eq 1 ] ; then
   break
else

   read -e word1 word2 word3 word4 word5

   if [ $S1 = $word1 ] ; then

       if [ $S2 = $word2 ] ; then 

           echo -e $word3 $word4 $word5\n > phonelist
       else	
          
            for WORD in `cat phonelist`
            do

         if [ $flag1 -eq 2 ] ; then
            echo $WORD
            break

         else	
            if [ $flag1 -eq 0 ] ; then

               if [ $WORD = $word2 ] ; then
                  flag1=1
               else
                 flag1=0
               fi

            else

               if [ $WORD = $word3 ] ; then
                   flag1=2
               else
                  flag1=0
               fi
             fi
          fi

          done
    else 

        echo "Incorrect command"

    fi

fi

done
```

and the compiling result

```
./phone: line 57: syntax error near unexpected token `else'
./phone: line 57: `	 else '
```

---

### Post by Lorin Ricker on 2011-03-18
See this (related) post-response for some help:

[http://ubuntuforums.org/showthread.php?p=10572561](http://ubuntuforums.org/showthread.php?p=10572561)

Your if-then-elses are likely improperly nested, or you've got mis-matched if...fi's.

BTW, bash is not a "compiled" language.  All the command "chmod +x phone" is doing is setting the user's (file owner's) execute (x) permission bit, so you can execute the script.

---

### Post by matt_symes on 2011-03-18
Hi

      ```
     else

               if [ $WORD = $word3 ] ; then
                   flag1=2
               else
                  flag1=0
               fi
             fi
          fi

          done
    else 

        echo "Incorrect command"

    fi
```

Your missing a fi instruction

```
           else

               if [ $WORD = $word3 ] ; then
                   flag1=2
               else
                  flag1=0
               fi
             fi
          fi

          done
    **fi**
    else 

        echo "Incorrect command"

    fi
```

Correct indentation would have make it obvious.

Kind regards

---

### Post by Dimitris1989 on 2011-03-18
i added the "fi" and it worked...thanks...

---

### Post by Dimitris1989 on 2011-03-28
hellow again!

i have the following code

```
#!/bin/bash
i=1
j=2
k=0

for WORD in `cat hitcount.txt`
do

        if [ $i -eq $j ] ; then
        MYARRAY1[$k]="$WORD"
        k=$(($k+1))
        j=$(($j+5))
        fi

i=$(($i+1))
done

i=1
j=5
k=0

for WORD in `cat hitcount.txt`
do

        if [ $i -eq $j ] ; then
        MYARRAY2[$k]="$WORD"
        k=$(($k+1))
        j=$(($j+5))
        fi

i=$(($i+1))
done

```

and here is hitcount.txt

```
1197979501.787 171.69.64.62 TCP_POSITIVE_HIT/200 GET
http://www.yahoo.com
1197979501.788 171.69.64.65 TCP_NEGATIVE_HIT/404 POST
http://www.yahoo.com
1197979501.805 171.69.64.62 TCP_POSITTIVE_HIT/200 POST
http://www.boo.org
1197979502.787 171.69.64.61 TCP_NEGATIVE_HIT/404 GET
http://www.bla.gr
1197979502.790 171.69.64.67 TCP_NEGATIVE_HIT/404 GET
http://www.yahoo.com

```

In array MYARRAY1 i store the IP addresses.
In array MYARRAY2 i store the websites.
I want to sort those two arrays and when i press the command

```
echo ${#MYARRAY1[*]}
```

the result to be

1```
71.69.64.61 171.69.64.62 171.69.64.62 171.69.64.65 171.69.64.67
```

or something like that.I have tried to do it by making a bubble-sort with no success. Any ideas??
Thanks in advance and sorry for the length of the post!

---

