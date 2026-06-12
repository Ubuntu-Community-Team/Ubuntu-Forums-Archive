---
title: "Bash script help!"
date: 2011-03-17
forum: General Help
---

### Post by wasd591 on 2011-03-17
I'm trying to make a automatic Wordpress installer script. It's autmattically defaulting to the else. Can you please tell me how to fix it up? Thanks, sorry for being a noob. :P

Script
```
#!/bin/bash
echo -n 'Enter website (without .com)> '
read DIRECTORY
if [ -d '/home/$DIRECTORY' ]; then
	echo 'Exists'
	echo 
	echo 'Downloading wordpress files...'
	cd '/home/$DIRECTORY'
	sudo wget -q http://wordpress.org/latest.tar.gz
	echo Extracting...
	sudo tar -zxf latest.tar.gz
	sudo mv /wordpress/* /home/$DIRECTORY
	# Just don't want to move to the root directory, oops!
	sudo rm -R /wordpress/*
	sudo rm latest.tar.gz
	sudo chmod -R 755 *
	echo Finished!
	echo Make sure to setup the MySQL...
	read -n1 -r -p "Press any key to quit..."
	exit
   else
	echo Incorrect directory!
fi
exit

```

---

### Post by gerowen on 2011-03-17
Not an expert on Bash, but shouldn't the else statement be outside of the if statement?  Here's some example code from one of my scripts where I use an if statement to manage the closing of the window if a user clicks "Cancel".  I googled most of the syntax and brain-dumped after I wrote the script, but hopefully this can serve as a good example to help get yours working.

P.S. The stars are where it censored out the name of a command that happens to also be a term that refers to a female body part.

```

#!/bin/bash
#Lit2PDF 10.11.30
#This is a script to automate converting a .lit
#file to a .pdf file using convlit, html2ps, and ps2pdf
#software packages.
#Marcus Dean Adams (marcusdean.adams@gmail.com)
rm -R -f lit2pdf-temp
echo ""
zenity --info --title="Lit2PDF" --text="Please select the file you wish to convert."
echo ""
infile=$(zenity --file-selection --filename=/home --title="Select a LIT file")
if [ $? == 0 ]
then
	title=$(zenity --entry --text "What is the title of the book?")
	if [ $? == 0 ]
	then
		echo ""
		zenity --info --title="Ready" --text="Conversion may take a long time depending on the length of the book.  Click OK to begin."
		mkdir lit2pdf-temp
		**** "$infile" lit2pdf-temp/html/
		html2ps lit2pdf-temp/html/*.htm > lit2pdf-temp/temp.ps
		ps2pdf lit2pdf-temp/temp.ps "lit2pdf-temp/$title.pdf"
		mv "lit2pdf-temp/$title.pdf" $HOME/Desktop
		rm -R -f lit2pdf-temp
	fi
fi

```

---

### Post by wasd591 on 2011-03-17
Thank You so much! Fixed it!

---

