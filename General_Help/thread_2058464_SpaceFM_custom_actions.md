---
title: "SpaceFM custom actions"
date: 2012-09-15
forum: General Help
---

### Post by DapperMe17 on 2012-09-15
Hi,

I've just replaced PCManFM with SpaceFM, so that I can use custom commands such as in Nautilus or Thunar.

I have a Robert's old "wipe" script, which I would like to call from SpaceFM, in order to wipe unneeded files. Alternatively, a script to do the same in SpaceFm would be awesome. 

Any help would be most appreciated!

Here is Robert's "nautilus" script...

> #!/bin/bash
#
#  Nautilus secure file deletion script v1.2
#  Written by Robert Pectol, July 2007 - [http://rob.pectol.com/myscripts](http://rob.pectol.com/myscripts)
#
#
#  CHANGELOG:
#
#  03/31/08 (bubfix) v1.2 - Included the, "-q" switch to fix the user
#  specified number of file wiping passes.  Thanks Martijn Markies for
#  pointing it out.
#
#
#  This  secure file deletion script  must be  called from  Nautilus!
#  Place this script in your  nautilus-scripts directory and make sure
#  it's executable  (chmod 775 this_script.sh)  and it will show up in
#  the,  "Scripts" menu when files are right-clicked  from within your
#  Nautilus file  manager.  Please report any bugs to [email]rob@pectol.com[/email].
#
#  This script requires the wipe command line utility to handle secure
#  file deletion.  If you don't have the wipe utility, you  can easily
#  install it by opening a shell and typing, "sudo apt-get install wipe"
#  at the  command  prompt.
#
#  This  program is free  software.  It  is distributed  in the hope
#  that it will be useful, but WITHOUT ANY WARRANTY; without even the
#  implied warranty of  MERCHANTABILITY or FITNESS  FOR A PARTICULAR
#  PURPOSE.  See the  GNU General Public  License for  more details.
#
######################################################################

###############################
#  User configurable options  #
###############################

# number of passes (how many times to overwrite the file with random data)
passes=15

###############################
#  End configurable options   #
###############################



####################################################
#  YOU SHOULDN'T MODIFY ANYTHING BELOW THIS LINE!  #
####################################################

# Set some script variables
the_file=$1
if [ "$NAUTILUS_SCRIPT_CURRENT_URI" == "x-nautilus-desktop:///" ]; then
	files_path=$HOME"/Desktop"
else
	files_path=`echo "$NAUTILUS_SCRIPT_CURRENT_URI" | sed -e 's/^file:\/\///; s/%20/\ /g'`
fi
gui=`which zenity`
secure_delete=`which wipe`

# Secure file deletion disclaimer
if [ ! -f ~/.sec_filedel_agreed ]; then
	dialog_title="Disclaimer!"
	dialog_type="--question"
	ackn1="By using this secure file deletion script, you acknowledge"
	ackn2="that you understand the following:  Once the file is deleted,"
	ackn3="it is gone.  That is, it is destroyed and cannot be recovered"
	ackn4="EVEN WITH FILE RECOVERY UTILITIES!!! You also acknowledge that"
	ackn5="you absolve the author of this script of any responsibility"
	ackn6="for accidental data loss due to your use of it, whatsoever."
	ackn7="You also acknowledge that you assume full responsibility for"
	ackn8="any and all data loss due to your use of it!  Select, 'OK' to"
	ackn9="acknowledge."
	ackn10="(NOTE: This notice will only be shown once unless you decline to acknowledge!)"
	feedback=`echo $ackn1 $ackn2 $ackn3 $ackn4 $ackn5 $ackn6 $ackn7 $ackn8 $ackn9 $ackn10 $ackn11 $ackn12`
	zenity --title "$dialog_title" "$dialog_type" --text "$feedback"
	if [ "$?" == "0" ]; then
		touch ~/.sec_filedel_agreed
		$gui --title "Enabled!" "--info" --text "OK!  You may now re-launch the script!"
	else
		$gui --title "Disabled!" "--info" --text "Then you should probably NOT use this script!"
	fi
	exit 0
fi

# Secure file deletion function
sec_file_del()
{
	# Prompt for confirmation
	dialog_title="Confirm"
	dialog_type="--question"
	feedback="Are you sure you want to securely delete $the_file?"
	feedback
	if [ "$yesorno" == "1" ]; then
		dialog_title="Cancelled"
		dialog_type="--info"
		feedback="Cancelled at your request!"
		feedback
		exit 0
	fi
	# Securely delete the file
	$secure_delete -q -Q $passes -ifFr "$files_path/$the_file" 2>&1 | $gui --title "Secure File Deletion" --progress --text="Securely deleting $files_path/$the_file..." --pulsate --auto-close
	# Check to see that the file got deleted
	if [ -a "$files_path/$the_file" ]; then
		result="$the_file could NOT be securely deleted!"
		dialog_title="Error!"
		dialog_type="--error"
		feedback=$result
		feedback
		exit 1
	else
		result="$the_file was securely deleted!"
		dialog_title="Success!"
		dialog_type="--info"
		feedback=$result
		feedback
	fi
}

# Feedback function
feedback()
{
	$gui  --title "$dialog_title" $dialog_type --text="$feedback"
	yesorno=$?
}

# Errors function
errors()
{
	if [ -x "$gui" ]; then
		result="The wipe command line utility was NOT found!"
	else
		result="Zenity NOT found.  This utility is required!; "
	fi
	echo $result
	dialog_title="Missing Required Tools!"
	dialog_type="--error"
	feedback=$result
	feedback
	exit 1
}

# Check for required tools
if [[ -x "$gui" && -x "$secure_delete" ]]; then
	sec_file_del
else
	errors
fi
exit 0

      

---

### Post by DapperMe17 on 2012-09-16
bump

---

