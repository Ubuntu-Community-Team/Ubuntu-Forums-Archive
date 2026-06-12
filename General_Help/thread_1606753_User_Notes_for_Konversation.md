---
title: "User Notes for Konversation"
date: 2010-10-26
forum: General Help
---

### Post by vis.15 on 2010-10-26
This is a script that I created for Konversation. This script allows you to select a Nick and then write some notes about that User. Here is the full list of commands for the script: (I call my script nn, because it is very easy to type in. So I will be calling the script with /nn)

/nn - Opens up Notes file for selected Nick and Inserts date and Time at the end of the notes file. 

/nn c - Checks to see if there is a notes file for the selected nick.

/nn t - Opens up the notes file for selected nick, but does NOT insert the date and time.

/nn l - List last user note's opened.

/nn n NICK - When in a PM or no nick is selected, allows you to manual open a users/nick notes.

/nn d - Delete Last Nick user's notes.

/nn d NICK - Deletes NICKs user notes file. (Version 4.0 Only.)

/nn tc - First checks to see if the Notes file exist. If not then displays a message saying it cannot open that file. If it does exist then opens the file in GEdit.

/nn tc NICK - Same as /nn tc but uses Nick instead. (Version 4.0 Only.)

/nn nc NICK or /nn c NICK (Version 4.0 Only.) - Manually checks if a User Note Exist.

/nn nt NICK or /nn t NICK (Version 4.0 Only.) - Manually open up User note and do not insert date.

/nn v - View Script Name, Author and Version.

/nn vs - Show the current channel /nn v.

/nn p - Add 1 Point to the current user Points.

/nn pp - Subtracts 1 Point to the current user Points.

```

#!/bin/bash
Version="4.0 Beta"
Author="Dis"
Name="Konversation User Notes Script"
#note: $1=Server, $2=Channel, $3=File, $4=t/c/tc/n/d/..., $5=Nick,
#note: t=No Date/Time, c=check, d=delete last nick opened. l=last nick, s=show messages in chat, sa=show all in chat, eg. errors. 

BB= #Turns Text Bold in IRC #0x02 = Bold
Num=0
#Global Vars For use inside Functions
Server=$1
Target=$2
File=$3
Var=$4
#if $5=*L* then log.
LN2=$5

function Update_Nick {
	LN=$LN2`echo ${File##*/}` #LN=Last nick/File Name; ##=last last part; *=*; /=split char
	Dir=`echo ${File%/*}` #Dir = Working Directory; %=first part;
	File=$Dir/$LN
	Nick=`echo ${LN%%-*}` #Nick=Nick Name
	Nick2=`echo ${LN##*-}` #Rest of LN
}

Update_Nick

if [[ "$Var" != *s* ]]; then
	cmd=info
elif [[ "$Var" == *s* ]]; then
	say2=say
	cmd="$say2 $Server $Target"
fi

if [ "$Var" != "i" ] && [[ "$Var" != *d* ]]; then
	echo "$LN" > $Dir/LN #saves file/nick into current working dir
fi
	
function Check_File {
	if [ -d $File ]; then #if Dir then exit.
		if [[ "$Var" != *sa* ]]; then
			qdbus org.kde.konversation /irc info "$BB""Error:$BB $Dir/$BB$Nick$BB-$Nick2 $BB""is a Directory$BB."
			exit; 
		else
			qdbus org.kde.konversation /irc say $Server "$Target" "$BB""Error:$BB $Dir/$BB$Nick$BB-$Nick2 $BB""is a Directory$BB."
			exit;
		fi
	fi
	if [ -e $File ]; then
		Exist="True" #if exist (ex) then True
		New_Line='\n' #for insert date
	elif [ ! -e $File ]; then
		Exist="False" #if not exist (ex) then False

		if [ "$1" != "No_Exit" ]; then #n=no error, if file does not exist;
			if [[ "$Var" != *sa* ]]; then
				qdbus org.kde.konversation /irc info "$BB""File:$BB $Dir/$BB$Nick$BB-$Nick2 $BB""does not exist$BB."
				exit;
			else
				qdbus org.kde.konversation say $Server "$Target" "$BB""File:$BB $Dir/$BB$Nick$BB-$Nick2 $BB""does not exist$BB."
				exit;
			fi
		fi
	else
		qdbus org.kde.konversation /irc error "An Unknown Error has Occurred."
		exit;
	fi
}

function OC_File { #OC = Open Close
	if [ "$Exist" == "False" ]; then
		CF="$BB""Created$BB $Dir/$BB$Nick$BB-$Nick2."
		qdbus org.kde.konversation /irc $cmd "$CF"
	fi

	qdbus org.kde.konversation /irc $cmd "$BB""Opened$BB $Dir/$BB$Nick$BB-$Nick2 in $Target. $KonInfo."
	gedit $File
	qdbus org.kde.konversation /irc $cmd "$BB""Closed$BB $Dir/$BB$Nick$BB-$Nick2 in $Target. $KonInfo."
}

function Insert_Date {
	echo -e `date +"%a, %b %d %r %Y %Z"`'\n' >> $File
}

function Remove_Points_Line {
	Last_Line=`tail -1 $File` #Get last line of $File
	if [[ $Last_Line == Points* ]]; then
		Num=`echo ${Last_Line:8}` # Len(Points: ) = 8
		sed '$d' < $File > $Dir/nn.tmp #Remove last line
		mv $Dir/nn.tmp $File
	fi
}

if [ "$Var" == "" ] || [ "$Var" == "n" ] || [ "$Var" == "s" ] || [[ "$Var" == *ns* ]]; then
	Check_File "No_Exit"
	
	if [ "$Exist" == "True" ]; then
		Remove_Points_Line
	fi
	
	Insert_Date
	echo -e "\n""Points: $Num" >> $File
	OC_File
	exit;
fi

case $Var in
*t*)
	if [[ "$Var" == *tc* ]]; then #Could place *c* before *t*, then do not need. Which is faster?
		Check_File 
	fi
	
	UU=`echo $4 | tr '[a-z]' '[A-Z]'`; #lower to upper case
	KonInfo="In Mode: $BB$UU$BB"

	OC_File
	exit;
	;;
*c*)
	Check_File
	
	if [ "$Exist" == "True" ]; then
		qdbus org.kde.konversation /irc $cmd "$BB""File:$BB $Dir/$BB$Nick$BB-$Nick2 $BB""exist$BB."
	fi
	exit;
	;;
*p*)
	Check_File "No_Exit"

	if [ "$Exist" == "True" ]; then
		Remove_Points_Line
	fi
	
	if [[ "$Var" == *pp* ]]; then #-1 Point
		Num=$((Num-1))
		PM="-"
	else
		Num=$((Num+1))
		PM="+"
	fi
	
	echo "Points: $Num" >> $File

	qdbus org.kde.konversation /irc $cmd "$BB$Nick$BB $PM""1 Point. $BB""Total Points: $Num"
	;;
*d*)
	File=$Dir/`cat $Dir/LN`

	Update_Nick
	Check_File
	rm $File
	qdbus org.kde.konversation /irc $cmd "$BB""File$BB $Dir/$BB$Nick$BB-$Nick2 was $BB""deleted$BB."
	;;
*l*)
	File=$Dir/`cat $Dir/LN`
	Update_Nick
	qdbus org.kde.konversation /irc $cmd "$BB""Last Nick$BB was $Dir/$BB$Nick$BB-$Nick2"
	;;
*i*)
	if [ "$4" == "is"  ]; then
		qdbus org.kde.konversation /irc say $Server "$Target" "/me is using $BB$Name$BB By: $BB$Author$BB version: $BB$Version"
	else	
		qdbus org.kde.konversation /irc info "$BB$Name$BB By: $BB$Author$BB version: $BB$Version"
	fi
	;;

esac

```

Here is the Script (OLD version):
```

#!/bin/bash
Version="3.5"
Author="Dis"
Name="Konversation User Notes Script"
#note: $1=Server, $2=Channel, $3=File, $4=t/c/tc/n/d, $5=Nick,
#note: t=No Date/Time, c=check, d=delete last nick opened
#feature: /nn n Nick on PM's or No Nick Selected; Done.
#feature: /nn l; list what's in LN Done.
#feature: /nn v/vs; version/version show in IRC; Done.
# /nn nc Manually check if Note Exist.
#/nn nd broken.

File=$3 #this is so, b/c positional parameters are very hard to change
BB= #Turns Text Bold in IRC #0x02 = Bold

if [[ "$4" == *v* ]]; then
    if [ "$4" == "vs"  ]; then
        qdbus org.kde.konversation /irc say $1 "$2" "/me is using $BB $Name $BB By: $BB $Author $BB v:$Version"
    else    
        qdbus org.kde.konversation /irc info "Is $BB $Name $BB By: $Author $BB v:$Version"
    fi
    exit;
fi

LN=`echo ${3##*/}` #LN=Last nick; ##=last last part; *=*; /=split char
Dir=`echo ${3%/*}` #Dir = Working Directory; %=first part;

if [[ "$4" != *d* ]] && [[ "$4" != *l* ]]; then
    echo "$5$LN" > $Dir/LN; #saves file/nick into current working dir
    
    if [[ "$4" == *n* ]]; then # && [[ "$5" != "" ]]
        File="$Dir/$5$LN"
        LN=`echo ${File##*/}`
        Dir=`echo ${File%/*}`
    fi
elif [[ "$4" == *d* ]] || [[ "$4" == *l* ]]; then
    File=$Dir/`cat $Dir/LN` #File = file/Last Nick Used
    if [[ "$4" == *l* ]]; then
        LN=`echo ${File##*/}`
        Dir=`echo ${File%/*}`
        qdbus org.kde.konversation /irc info "Last Nick: $Dir/$BB $LN $BB"
        exit;
    fi
fi

if [ -e $File ]; then
    ex="t" #if exist (ex) then True
    NL='\n'
elif [ ! -e $File ]; then
    ex="f" #if not exist (ex) then False
    CF="$BB Created $BB File: $Dir/$BB $LN" 
else
    qdbus org.kde.konversation /irc error "An Unknown Error has Occurred."
    exit;
fi

if [[ "$4" == *t*  ]]; then #spaces matter! Just like regular commands!
    UU=`echo $4 | tr '[a-z]' '[A-Z]'`; #lower to upper case
    KonInfo="In Mode: $BB $UU"
    
    if [[ "$4" == *tc* ]]; then
        if [ "$ex" == "f" ]; then
            qdbus org.kde.konversation /irc info "File: $Dir/$BB $LN does not exist"
            exit;
        fi
    fi
else #&&=to make new file, e.g. /nn n dis; || b/c check fails, /nn c
    if [ "$ex" == "t" ] && [[ "$4" == *c* ]]; then
        qdbus org.kde.konversation /irc info "File: $Dir/$BB$LN exist"
        exit;
    elif [ "$ex" == "t" ] || [[ "$4" != *c* ]]; then
        if [[ "$4" != *d* ]]; then
            echo -e $NL`date +"%a, %b %d %r %Y %Z"`'\n' >> $File
        fi
    fi
    if [ "$ex" == "f" ] && [ "$5" == "" ]; then
        if [[ "$4" == *c* ]]; then
            ERR='info'
        else
            ERR="$BB error $BB"
        fi
        qdbus org.kde.konversation /irc $ERR "File: $Dir/$BB $LN does not exist"
        exit;
    fi
fi

if [[ "$4" != *d* ]]; then
    if [ "$ex" == "f" ]; then
        qdbus org.kde.konversation /irc info "$CF"
    fi
    
    qdbus org.kde.konversation /irc info "$BB Opened $BB up: $Dir/$BB $LN $BB from $2 $KonInfo";
    gedit $File;
    qdbus org.kde.konversation /irc info "$BB Closed: $BB $Dir/$BB $LN $BB from $2 $KonInfo";
elif [[ "$4" == *d* ]]; then
    rm $File
    qdbus org.kde.konversation /irc info "File $Dir/$BB$LN was deleted."
else
    qdbus org.kde.konversation /irc error "Unknown Command."
fi


```To implement this into Konversation:
[LIST=1]
[*]Put the script into: /usr/share/kde4/apps/konversation/scripts/
To do this: Open up a terminal and type in "sudo cp nn /usr/share/kde4/apps/konversation/scripts/nn" (with out the quotes)
[*]In Konversation go to: Settings, then Configure Konversation, Then Quick Buttons
[*]Press the New button. Enter a name in, I use Notes. Then in the command action box: Type in: /exec nn /home/NAME/Notes/%u-%c.notes%n
Then click Apply.
where: NAME = your user name, and nn = the script name
Also, /Notes/%u.notes can be changed to what ever you like
[*]Now go to Chat Window, and make sure "Show Channel nick list and Quick Buttons" is  checked.
[*]Now click OK. Now you should see a button under the nick list called Notes.
[*]Just select the nick you want to write a note about then click on Note.
[/LIST]

Notes: I am still working on it. The next version will be 4.0 and will be modular. That is, everything will have it's own function. (If you don't think it would be a good idea, then please say so.)
Also, if you would like another feature/function, just ask and I will see if I can implement it in.

---

### Post by vis.15 on 2010-11-08
Version 4.0 Beta is here. Tell me what you think. Thank you.

---

### Post by vis.15 on 2010-11-13
New feature added today! Allows you to add and subject points from a user. 

Basically what it does, is it adds a line to the end of the user notes for that user that says "Points: X" where X is how many points they have.

usage: 

/nn p - adds one point
/nn pp - subtracts one point

Tell me what you think. Should I add adding multiple points?

---

### Post by vis.15 on 2010-11-19
Version 4.0 has been updated.

Major Bug fixes in version 4.0 beta.
Minor bug fixes.

Version 4.0 Beta seems to be working perfectly. Though I have not 100% tested the current version.

---

