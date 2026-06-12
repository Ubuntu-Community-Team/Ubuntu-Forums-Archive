---
title: "What is wrong with this script?"
date: 2010-04-13
forum: General Help
---

### Post by nmobrien4 on 2010-04-13
```
#removes items from ~/Desktop

CORRECT="4444" 

echo "Please enter Password:"
read PASSWORD

if [ "$PASSWORD" == "$CORRECT" ]; then
    
    
    echo "Password Validated"
else
    
    echo "Invalid Password"
    exit
    

fi
    
if [ -f "~/Desktop/*" ] then;
    
    echo
    echo
    echo "Removing Desktop items..."
    echo
    echo
    rm -r /home/nick/Desktop/*
    echo
else
    echo "There are no items in Desktop"
       
fi
```
When I run it I get:

****@****-laptop:~$ rmdes
Please enter Password:
4444
Password Validated
/home/****/bin/rmdes: line 29: syntax error near unexpected token `else'
/home/****/bin/rmdes: line 29: `else'


EDIT: Ah I see now that I misplaced the semicolon on the second if statement.

---

