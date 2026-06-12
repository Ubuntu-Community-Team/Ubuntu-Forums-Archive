---
title: "Bash Script"
date: 2011-03-17
forum: General Help
---

### Post by wasd591 on 2011-03-17
Help! New to bash and I'm trying to make an automatic Wordpress installer :confused:. Gives the following error:

./wpinstall.bash: line 119: syntax error near unexpected token `fi'
./wpinstall.bash: line 119: `           fi'

Here's the script:

```
#!/bin/bash
echo -n 'Enter website (with .com etc...)> '
read SITE
echo -n 'Enter website (without .com)> '
read DIR

function quit
{
	exit 2
}

if [ -d /home/$DIR/public_html ];
then

	echo ------------------------------
	echo ----Wordpress Installation----
	echo ------------------------------
 	echo Downloading...
	cd /home/$DIR
	sudo wget -q http://wordpress.org/latest.tar.gz
	echo Extracting...
	sudo tar -zxf latest.tar.gz
	sudo mv wordpress/* /public_html/
	echo Cleaning up...
	sudo rm -R wordpress/
	sudo rm latest.tar.gz
	sudo chmod -R 755 public_html/*
	echo Wordpress installed Successfully!
	
	echo ------------------------------
	echo ------MySQL Installation------
	echo ------------------------------
	
	function register
	 {
		echo -n 'Enter database name> '
		read DBNAME
		echo -n 'Enter username for database> '
		read USRNAME
		echo -n 'Enter password for database> '
		read PASSWD
		echo -n 'Re-enter password> '
		read PASSWDCHK
	}

	if [ "$PASSWD" -eq "$PASSWDCHK" ];
	then
		echo Passwords are equal.
	else
		echo Passwords are different
	fi
	
	CHECK=""

	while [ "$CHECK" -eq "" ];
		echo ---------------------------
		echo Checking Settings...
		echo ---------------------------
		echo Are these correct?
		echo Username: $USRNAME
		echo Password: $PASSWD
		echo Database: $DBNAME
		echo ---------------------------
		echo -n 'Are these correct? y/n> '
		read CHECK
	
		until [ $CHECK -eq "y" ];
		do
			echo Oh noes!
			echo Let's try again...
			register
		fi
	
		echo Perfect... we will run the folllowing commands:
		MYSQL1="CREATE DATABASE $DBNAME;"
		MYSQL2="CREATE USER '$USRNAME'@'%' IDENTIFIED BY '$PASSWD';"
		MYSQL3="GRANT ALL PRIVILEGES ON $DBNAME.* TO '$USRNAME'@'%';"
		MYSQL4="FLUSH PRIVILEGES;"
		echo $MYSQL1
		echo $MYSQL2
		echo $MYSQL3
		echo $MYSQL4
		
		OK=""
		until [ $OK -eq "y" ]; do
			echo -n 'Is this right? y/n > '
			read OK
		fi

		echo Running command 1-4...
		MYSQLRUN="${MYSQL1}${MYSQL2}${MYSQL3}${MYSQL4}"
		echo Please enter root password for MySQL.
		mysql -u root -p -e "$MYSQLRUN"
		
		# Check MySQL for errors...
		
		if [ "$?" -eq 1 ];
		then
			# Yep
			echo MySQL General Error!
			quit
		else
			# Nope
			echo Command completed!

			echo ------------------------------
			echo ---------FINSIHED!------------
			echo ------------------------------
			echo Goto $SITE now and configure
			echo wordpress with the username
			echo and password you supplied for
			echo MySQL.


else
	echo Domain doesn't exist in this system.
	exit 3

		fi
	fi
fi
exit 0
```

---

### Post by TeoBigusGeekus on 2011-03-17
You have 3 ifs and 6 fis.

---

### Post by wasd591 on 2011-03-17
Still broken. :( Can you change it for me please?

---

### Post by SeijiSensei on 2011-03-17
```

		until [ $CHECK -eq "y" ];
		do
			echo Oh noes!
			echo Let's try again...
			register
		fi
	


```

You need to use "done" when matching "do".

---

### Post by sisco311 on 2011-03-17
I deleted some lines which were irrelevant for debugging...

```

#!/bin/bash
echo -n 'Enter website (with .com etc...)> '
read SITE
echo -n 'Enter website (without .com)> '
read DIR

function quit
{
	exit 2
}

if [ -d /home/$DIR/public_html ];
then

	function register
	{
		echo 2
	}

	if [ "$PASSWD" -eq "$PASSWDCHK" ];
	then
		echo Passwords are equal.
	else
		echo Passwords are different
	fi

	while [ "$CHECK" -eq "" ];
	[color=red]do[/color]
		until [ $CHECK -eq "y" ];
		do
			register
		[color=red]done[/color]
	
		until [ $OK -eq "y" ]; do
			read OK
                [color=red]done[/color]

		if [ "$?" -eq 1 ];
		then
			quit
		else
			echo MySQL.
		[color=red]fi[/color]
	[color=red]done[/color]
else
	[color=red]echo Domain doesn\'t exist in this system.[/color]
	exit 3

[color=red]#		fi[/color]
[color=red]#	fi[/color]
fi
exit 0

```

---

### Post by wasd591 on 2011-03-17
I think I fixed everything you told me to, now I'm getting this:
line 117: unexpected EOF while looking for matching `"'
line 125: syntax error: unexpected end of file

Modified code:
```

#!/bin/bash
echo -n 'Enter website (with .com etc...)> '
read SITE
echo -n 'Enter website (without .com)> '
read DIR

function quit
{
    exit 2
}

if [ -d /home/$DIR/public_html ];
then
    echo ------------------------------
    echo ----Wordpress Installation----
    echo ------------------------------
     echo Downloading...
    cd /home/$DIR
    sudo wget -q http://wordpress.org/latest.tar.gz
    echo Extracting...
    sudo tar -zxf latest.tar.gz
    sudo mv wordpress/* /public_html/
    echo Cleaning up...
    sudo rm -R wordpress/
    sudo rm latest.tar.gz
    sudo chmod -R 755 public_html/*
    echo Wordpress installed Successfully!
    
    echo ------------------------------
    echo ------MySQL Installation------
    echo ------------------------------
    
    function register
     {
        echo -n 'Enter database name> '
        read DBNAME
        echo -n 'Enter username for database> '
        read USRNAME
        echo -n 'Enter password for database> '
        read PASSWD
        echo -n 'Re-enter password> '
        read PASSWDCHK
    }

    if [ "$PASSWD" -eq "$PASSWDCHK" ];
    then
        echo Passwords are equal.
    else
        echo Passwords are different
    fi
    
    CHECK=""

    while [ "$CHECK" -eq "" ];
    do
        echo ---------------------------
        echo Checking Settings...
        echo ---------------------------
        echo Are these correct?
        echo Username: $USRNAME
        echo Password: $PASSWD
        echo Database: $DBNAME
        echo ---------------------------
        echo -n 'Are these correct? y/n> '
        read CHECK
    
        until [ $CHECK -eq "y" ];
        do
            echo Oh noes/!
            echo "Let's try again..."
            register
        done
    
        echo Perfect... we will run the folllowing commands:
        MYSQL1="CREATE DATABASE $DBNAME;"
        MYSQL2="CREATE USER '$USRNAME'@'%' IDENTIFIED BY '$PASSWD';"
        MYSQL3="GRANT ALL PRIVILEGES ON $DBNAME.* TO '$USRNAME'@'%';"
        MYSQL4="FLUSH PRIVILEGES;"
        echo $MYSQL1
        echo $MYSQL2
        echo $MYSQL3
        echo $MYSQL4
        
        OK=""
        until [ $OK -eq "y" ]; do
            echo -n 'Is this right? y/n > '
            read OK
        done

        echo Running command 1-4...
        MYSQLRUN="${MYSQL1}${MYSQL2}${MYSQL3}${MYSQL4}"
        echo "Please enter root password for MySQL."
        mysql -u root -p -e "$MYSQLRUN"
        
        # Check MySQL for errors...
        
        if [ "$?" -eq 1 ];
        then
            # Yep
            echo MySQL General Error!
            quit
        else
            # Nope
            echo Command completed!

            echo ------------------------------
            echo ---------FINSIHED!------------
            echo ------------------------------
            echo Goto $SITE now and configure
            echo wordpress with the username
            echo "and password you supplied for"
            echo MySQL.
        fi
    done
else
    echo Domain doesn\'t exist in this system."
    exit 3

#        fi
#    fi
fi
exit 0
```

---

### Post by Lorin Ricker on 2011-03-18
What text editor are you using for this bash script? gedit? emacs? Or an IDE?

Good editors are syntax-sensitive, paying attention to the "shebang" 1st-line (**!#/bin/bash**, etc.) and will color language/syntax elements as they match (**" "**, **if then else fi**, **while do done**, **{ }**, etc.), to help you detect mis-matched open-close elements.  Learn to watch and comprehend the color changes as you type in statements and other elements -- this will "follow you closely", and will help you detect mis-match errors *well before* they cause syntax errors at run-time.

Also watch any semicolons "**;**" you may need (bash is pretty peculiar in this regard, unlike most true programming languages)... a missing semi can get you into syntax-error trouble too.

You've written a pretty big script for your "first go", and you're getting the "classic" syntax errors which indicate mis-matched quotes, parens **( )**, brackets **[ ]**, curlies { }, **if**...**fi**, **while**...**do**...**done**, **case**...**esac**, etc.

When you see error diagnostics like

> 
line 117: unexpected EOF while looking for matching `"'
line 125: syntax error: unexpected end of file
or
> 
./wpinstall.bash: line 119: syntax error near unexpected token `fi'
./wpinstall.bash: line 119: `           fi'
it always means that you've got mis-matched syntax elements.  Once the language parser sees an opening-element, it's gonna look  determinedly for the matching closing-element, and will run right off  the end-of-file if it fails to find it.

Go to the first line# indicated ("line 117") and start looking there for the opening-element in question, whether a quote (single or double), or an if-statement (for the above two examples -- or whatever the error message indicates).

Then **scan** ***carefully*** **forward** looking for the mis-match, a missing closing element.  With practice comes familiarity, and you'll start learning to spot these things more quickly on your own.

It helps to type things into your script in small elements, too -- for example, rather than starting a long **if-then-else-fi** by typing just the first line:

```
  if [ -z "$var" ]; then
```and then blasting away at a long body of statements... and then forgetting to put in the closing

```
  fi
```try entering the "husk" of the statement, the whole syntax, first:

```

  if [ z "$var" ]; then
  else
  fi

```and then go back and fill in the "**then**" statement lines, followed by the "**else**" statements, into that structure, and at the correct level of indents.  This way, you're building your compound statements "inside-out" as it were.

You can then do this for each nested language structure (**while**s, **until**s, **case**s, etc.), always keeping things matched and never getting confused (unless you delete something unwittingly!).  I usually also type both opening & closing quote marks, parens, etc., like this: **""** or **( )** -- and then reposition my edit-cursor inside 'em to fill in the guts.

Little things like this help keep me sane -- in ***any*** language, not just bash scripts!  Hope this helps a bit!

---

### Post by TeoBigusGeekus on 2011-03-18
```
echo Domain doesn\'t exist in this system."
```

Should be

```
echo "Domain doesn\'t exist in this system."
```

+1 for a good text editor with syntax highlighting.

---

