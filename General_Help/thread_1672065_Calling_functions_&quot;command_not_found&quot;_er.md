---
title: "Calling functions &quot;command not found&quot; error."
date: 2011-01-20
forum: General Help
---

### Post by stamoulohta on 2011-01-20
I wrote the following script to organize my music files and to learn a bit more about bash.

My problem is, now that I'm almost over the first version, that functions which are surely spelled correctly and were recognized in the past, are giving me the "command not found" error!

Sorry for posting the whole script but I'm far from pinpointing the problematic code...
```
#!/bin/bash


# This is a script for moving tagged files into organized directory trees.

##### Variables

filenum=0
dirnum=0


##### Functions

function move_files
{
	path_tree="$out_dirkry/$gentre/$artist/$album"
	file_nm=$(echo $track_num-$title | sed 's/ /_/g')
	path_tree=$(echo $path_tree | sed 's/ /_/g')

	if [ $_tmcn_ = "t" ]; then
		echo "Testing : $new_file"
		echo "mv" "$new_file" "$path_tree/$file_nm.mp3" # EXTENTION WAY???
	elif [ $_tmcn_ = "m" ]; then
		echo "Moving : $new_file"
		mkdir -p "$path_tree"
		mv "$new_file" "$path_tree/$file_nm.mp3"
	elif [ $_tmcn_ = "c" ]; then
		echo "Copying : $new_file"
		mkdir -p "$path_tree"
		cp "$new_file" "$path_tree/$file_nm.mp3"
	elif [ $_tmcn_ = "n" ]; then 
		echo -e "Error in line #32\\n"; exit 1
	else 
		echo -e "Error in line #34\\n"; exit 1
	fi 

}	# end of move_files

function count_files
{
	countf=$(find $dirkry -type f | wc -l) # just counts lines
	countd=$(find $dirkry -type d | wc -l) #        -"-
	filenum=$(($filenum + $countf))
	dirnum=$(($dirnum + $countd))

	if [ $_tmcn_ = "n" ]; then
		test_file
	fi
	
}	# end of count_files

function create_dirkry
{
	echo -ne \\n"$out_dirkry does not exist. Create it? (y/n) :"
	read yesno
	case $yesno in
		y | Y )		mkdir $out_dirkry 
				if [ $? = 0 ]; then
					test_file
				else
					echo "Unable to create output directory."
					echo "Exiting program."; exit
				fi
				;;
		n | N )		yes_prsd
				;;
		* )		echo -e \\n "\"$yesno\" is not a valid input."; create_dirkry
	esac
}	#end of create_dirkry

function one_out_dir
{
	innu=0

	for indir in $out_dirkry; do
		innu=$(($innu + 1))
	done

	if [ "$innu" != "1" ]; then 
		echo -e \\n"You may specify only one directory."; yes_prsd
	fi
}	# end of one_out_dir

function yes_prsd
{
	echo -ne \\n"Give path for output directory. > "
	read out_dirkry
		one_out_dir	
	if [ -d $out_dirkry ]; then 
		test_file
	else 
		create_dirkry
	fi
}
function pro_sid
{
	echo -ne \\n"Will now process "$filenum" files in "$dirnum" directories. Proceed? (y/n) :"
	read yesno 
	case $yesno in
		y | Y )		yes_prsd
				;;
		n | N )		echo -e \\n"Exiting program."\\n; exit 1
				;;
		* )		echo -e \\n "\"$yesno\" is not a valid input."; pro_sid
	esac
}	# end of pro_sid

function test_file
{
	unpro_num=0
	pro_num=0
	find $dirkry -type f | while read new_file; do

		mp3info -x "$new_file" > /home/$USER/temp_tech 2>&1

		if [ $? = 0 ]; then 
			if [ $_tmcn_ = "n" ]; then
				pro_num=$(($pro_num + 1))
				echo "$new_file is valid"
			else readtag_file
			fi

		else 
		unpro_num=$(($unpro_num + 1))
		echo -e \\n"$new_file is not valid"

	fi
	
	rm /home/$USER/temp_tech

	done

	if [ $_tmcn_ = "n" ]; then
		menu_count
	fi
}	#end of test_file

function readtag_file   # This requires the mp3info package to be installed!!
{
	num_id="0"
	ORIG_IFS="$IFS"
	IFS=","
	
	for organ_tree in $(mp3info -p "%g,%a,%l,%n,%t" "$new_file"); do
		num_id=$(($num_id + 1))
	
		case $num_id in

			1 )	if [ -n "$organ_tree" ]; then
					gentre="$organ_tree"
				else
					gentre="unknown"
				fi
				;;
			2 )	if [ -n "$organ_tree" ]; then
					artist="$organ_tree"
				else
					artist="unknown"
				fi
				;;
			3 )	if [ -n "$organ_tree" ]; then
					album="$organ_tree"
				else
					album="unknown"
				fi
				;;
			4 )	if [ -n "$organ_tree" ]; then
					track_num="$organ_tree"
				else
					track_num="#"
				fi
				;;
			5 )	if [ -n "$organ_tree" ]; then
					title="$organ_tree"
				else
					title="unknown"
				fi
				
				move_files
				;;
			* )	echo "Error! More tags than format alows."; exit 1
		esac
	
	done

	IFS="$ORIG_IFS"
} 	# end of reatag_files

function menu_count
{
	cat << _EOF_
	Total files = $filenum
	Total directories = $dirnum
	    _________________

	Files that can be processed = $pro_num
	Files that can't be processed = $unpro_num
	
	_EOF_

	exit
}	# end of menu_count

function beg_in
{
	echo -ne \\n"Give path(s) to input directory. > "
	read paths

	for dirkry in $paths; do
		if [ -d $dirkry ]; then
			echo -e \\n"$dirkry is a valid path."
			count_files; pro_sid
		else
			echo -e \\n"$dirkry is NOT a valid path!\\nTry again."
			beg_in
		fi
	done
}	# end of beg_in

function short_menu
{
	if [ $file_type = "video files" ]; then
		echo -e \\n"Video files are not supported as of yet!\\n"; exit 1
	elif [ $file_type = "music files" ]; then
		case $_tmcn_ in 
			t )	beg_in
				;;
			m )	beg_in
				;;
			c )	beg_in
				;;
			n )	beg_in
				;;
			* )
		esac
	fi
}

function sub_sp_menu
{
	cat<<_EOF_
-----------------------------------------------------------------------
	Choose one of the following tasks for $file_type.

		"t"	- For testing files outcome.

		"m"	- For actual moving of files.

		"c"	- For copying of files (recomended)

		"n"	- For printing the total number of files in 
			  parent directory and the total number of 
			  files that can be processed and moved.
_______________________________________________________________________
_EOF_
	echo -n " > "
	read menu_tmcn

	case $menu_tmcn in
		t | T ) 	_tmcn_="t"
				;;
		m | M )		_tmcn_="r"; echo -e \\n"Don't you love your $file_type?\\nBetter choose something else for now ;)"; sub_sp_menu
				;;
		c | C )		_tmcn_="c"
				;;
		n | N )		_tmcn_="n"
				;;
		* )		clear; echo -e \\n"\"$menu_trc\" is not a valid option"\\n; sub_sp_menu
	esac

}	# end of sub_sp_menu

function splash_menu
{
	cat <<_EOF_
=======================================================================
	This script moves files from one or more parent directories to
     the choosen output directory and organizes them in subdirectories 
     acording to their tags. Choose one of the following options.

		"v"	- For video files organization.

		"m"	- For music files organization.

		"h"	- For printing help message and exiting.
_______________________________________________________________________

_EOF_
	echo -n " > "
	read menu_vmh

	case $menu_vmh in
		v | V ) 	file_type="video files"; sub_sp_menu
				;;
		m | M )		file_type="music files"; sub_sp_menu
				;;
		h | H )		prnt_hlp
				;;
		* )		clear; echo -e \\n"\"$menu_vmh\" is not a valid option"\\n; splash_menu
	esac
}	# end of splash_menu

function prnt_hlp
{
	echo -e \\n"Help is not yet available."\\n; exit
}	# end of prnt_hlp
clear

splash_menu

echo
exit
```

I hope that someone will take the time to help me out and I thank you in advance!

cheers
g.

---

