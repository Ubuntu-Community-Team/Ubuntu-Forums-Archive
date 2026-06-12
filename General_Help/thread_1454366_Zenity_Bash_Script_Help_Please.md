---
title: "Zenity Bash Script Help Please"
date: 2010-04-14
forum: General Help
---

### Post by skula on 2010-04-14
Hi Friends,

I am new to the world of unix and scriping in general, below is a script i wrote in bash and i wish to translate into zenity... all my effort has proved in vain, i have spent hours trying to do this but i just ian't successful.. the command line code is ok... i just need help to turning this into zenity

```

#!/bin/bash 
#!bin/bash
# paintmath.sh 
#Programmed By skula

#declared and asign variable option the value of 5
option=5

echo " ***SACal PaintMath***"
echo "1. Surface Area Of Sphere"
echo "2. Surface Area Of Cone"
echo "3. Surface Area Of Cylinder"
echo "4. Exit"

#loop thru condition while menu option 1-4 is processed 
while [ "$option" = 5 ]
do

#read user option
read option

#option if statemeny


 if [ "$option" = 1 ]
 then
 clear
 echo "You have choosen to calculate surface area of a sphere"
 #formula for  surface area of sphere is 4IIr^2
 #where r is radius of sphere and II(p) = 3.142
 
 #read radius input
 echo "Enter Radius of the sphere"
 read r
 
 for p in 3.142
 do
 

 Result=`echo "(4 * $p) * $r^2" |bc`
 
 echo "The Surface area of the calculated sphere is $Result"
 
 done
 
    
    
    elif [ "$option" = 2 ]
    then
    clear
         echo "You have choosen to calculate surface area of cone"
         
 #formula for  surface area of cone is IIrs + IIr^2
 #where r is radius of sphere, s length of cone and II(p) = 3.142
 
 p=3.142
 #read radius input
 echo "Enter Radius of the cone"
 read radius
 
 echo "Enter length of the cone"
 read length
 
  Result=`echo "($p * $radius * $length) + ($p * $radius^2)" |bc`
 
 echo "The Surface area of the cone is $Result"
 
    
    elif [ "$option" = 3 ]
    then
    clear
    echo "You have choosen to calculate surface area of cylinder" 
    
    
    #formula for  surface area of cylinder is 2IIr^2 + 2IIrh
 #where r is radius of cylinder, h is height of cylinder and II(p) = 3.142
 
 #read radius input
 echo "Enter Radius of the Cylinder"
 read radius
 
 echo "Enter height of cylinder"
 read height
 
 for p in 3.142
 do
 

 Result=`echo "(2 * $p * $radius^2) + (2 * $p * $radius * $height)" |bc`
 
 echo "The Surface area of the cylinder is $Result"
 
 done
 
    
     elif [ "$option" = 4 ]
    then
    echo "thank you for using paintmath pro"
    exit
    
    
    else
    clear
    echo "Please choose option 1 - 4 from the menu"
    echo "1. Surface Area Of Sphere"
    echo "2. Surface Area Of Cone"
    echo "3. Surface Area Of Cylinder"
    echo "4. Exit"
    
 fi

 done

```the above script is working perfectly in command line interface... my problem is translating this into zenity ... please assist me on this... i have tried all i can and i am beginning to get fed up.

---

### Post by kerry_s on 2010-04-14
what i do is just keep a manpage of zenity open so i can see the options. play with it a bit, try the different things to see what it does.

first you need to break down your script to where you can use a zenity gui. whats parts you want to see.

so from the top, looks like you need a selection, a --list, so scroll down the manpage & check out the options:

```

zenity --list --text="SACal PaintMath" --column="Select Option"

```
(that will give you a window with title & column header, try it)

then add your options:
```

zenity --list --text="SACal PaintMath" --column="Select Option" **"1. Surface Area Of Sphere" "2. Surface Area Of Cone" "3. Surface Area Of Cylinder" "4. Exit"**

```
(once again try it)

looks like you might want to put some height & width on that:
```

zenity --list **--height="300" --width="300"** --text="SACal PaintMath" --column="Select Option" "1. Surface Area Of Sphere" "2. Surface Area Of Cone" "3. Surface Area Of Cylinder" "4. Exit"

```
(try it)

then you just use the results for the commands you want to run.

example:
```

if [ "$?" == "1. Surface Area Of Sphere" ]; then
  zenity --info --text="1. Surface Area Of Sphere"
  notify-send "1. Surface Area Of Sphere"
fi

```

i usually use notify-send instead of the command when i'm making the script. you can also use zenity for that, if you don't have notify-send installed.

just work your way down.

---

### Post by skula on 2010-04-14
> **kerry_s said:**
> what i do is just keep a manpage of zenity open so i can see the options. play with it a bit, try the different things to see what it does.

first you need to break down your script to where you can use a zenity gui. whats parts you want to see.

so from the top, looks like you need a selection, a --list, so scroll down the manpage & check out the options:

```

zenity --list --text="SACal PaintMath" --column="Select Option"

```(that will give you a window with title & column header, try it)

then add your options:
```

zenity --list --text="SACal PaintMath" --column="Select Option" **"1. Surface Area Of Sphere" "2. Surface Area Of Cone" "3. Surface Area Of Cylinder" "4. Exit"**

```(once again try it)

looks like you might want to put some height & width on that:
```

zenity --list **--height="300" --width="300"** --text="SACal PaintMath" --column="Select Option" "1. Surface Area Of Sphere" "2. Surface Area Of Cone" "3. Surface Area Of Cylinder" "4. Exit"

```(try it)

then you just use the results for the commands you want to run.

example:
```

if [ "$?" == "1. Surface Area Of Sphere" ]; then
  zenity --info --text="1. Surface Area Of Sphere"
  notify-send "1. Surface Area Of Sphere"
fi

```i usually use notify-send instead of the command when i'm making the script. you can also use zenity for that, if you don't have notify-send installed.

just work your way down.



thank you for working me through dis... the step by step approach u explain is amazing.... i have worked the menu choice as u showed me and i hav entered the first block of code to perform the first option but still not got that
```

zenity --height="300" --width="300" --list --title="Paint Math Pro" --column="Select calculation to perform" "1. Surface Area Of Sphere" "2. Surface Area Of Cone" "3. Surface Area Of Cylinder" "4. Exit"

if [ "$?" == "1. Surface Area Of Sphere" ]; then

  zenity --info --text="1. Surface Area Of Sphere"
  #read user option
read option

#option if statement

 zenity -- info --text="You have choosen Surface Area of sphere
 #formula for  surface area of sphere is 4IIr^2
 #where r is radius of sphere and II(p) = 3.142
 
 #read radius input
 echo "Enter Radius of the sphere"
 read r
 
 for p in 3.142
 do
 

 Result=`echo "(4 * $p) * $r^2" |bc`
 
 echo "The Surface area of the calculated sphere is $Result"
 
fi

```

what i am trying to achieve is this... when the user runs the script and the first menu option is displace in zenity, i want a scenerio were by i choose the first option down to the last for the codes to execute in zentiy interface

eg.. if i select option and click ok, i want the it to show zenity info dialog saying i have selected option one.
and if i clic ok to confirm selection of option 1 , i would like the a zenity dialog saying enter the radius of the sphere in a zenity text box input. and when i enter the input and click ok, the script should excute with a follow up zenity dialog showing the result of the calcution..



thanx for yor assistance.... this is what i am trying to achieve for each individual menu.. i have got the calculation scripts working but only to implement it in zenity that eludes  me bigtime.


thank again for your help

---

### Post by kerry_s on 2010-04-14
i'll have a go, but math ain't my thing. :lolflag:

i'm trying to understand the math part right now.

i'll get back to you.

---

### Post by kerry_s on 2010-04-14
can you give this a try & see if i got the first 1 right:

```

#!/bin/bash 

sel=`zenity --height="300" --width="300" --list --title="Paint Math Pro" --column="Select calculation to perform" "Surface Area Of Sphere" "Surface Area Of Cone" "Surface Area Of Cylinder"`

if [ "$sel" == "Surface Area Of Sphere" ]; then
	num=`zenity --entry --text="Enter Radius of the sphere"` 
	result=`echo "(4 * 3.142) * $num^2" |bc`
	zenity --info --text="$result"


elif [ "$sel" == "Surface Area Of Cone" ]; then
	zenity --info --text="Surface Area Of Cone"

elif [ "$sel" == "Surface Area Of Cylinder" ]; then
	zenity --info --text="Surface Area Of Cylinder"
	
fi
exit 0



```

if that works just use the same for the other 2, just change the "echo *" to the 1's in your script.

---

### Post by skula on 2010-04-15
> **kerry_s said:**
> can you give this a try & see if i got the first 1 right:

```

#!/bin/bash 

sel=`zenity --height="300" --width="300" --list --title="Paint Math Pro" --column="Select calculation to perform" "Surface Area Of Sphere" "Surface Area Of Cone" "Surface Area Of Cylinder"`

if [ "$sel" == "Surface Area Of Sphere" ]; then
    num=`zenity --entry --text="Enter Radius of the sphere"` 
    result=`echo "(4 * 3.142) * $num^2" |bc`
    zenity --info --text="$result"


elif [ "$sel" == "Surface Area Of Cone" ]; then
    zenity --info --text="Surface Area Of Cone"

elif [ "$sel" == "Surface Area Of Cylinder" ]; then
    zenity --info --text="Surface Area Of Cylinder"
    
fi
exit 0



```if that works just use the same for the other 2, just change the "echo *" to the 1's in your script.




thank u for stopping by to help me... i still have not got this code working.... i tried to follow the example u gave down but still wen i click ok of the choosen option i want to perform , instead of a dialog option to continue and ask for user input , the scri[t just exits...and perform no forther option....


i tied using case statement instead of the if and elif statmemnt and i still arrived at the same thing with code not proceeding to do further action than just terminating

```

option=`zenity --height="300" --width="300" --list --title="Paint Math Pro" --column="Select calculation to perform" "1. Surface Area Of Sphere" "2. Surface Area Of Cone" "3. Surface Area Of Cylinder" "4. Exit"`

case $? in
       
       sphere)
    radius=`zenity --entry --text="Enter Radius of the sphere"` 
    p=3.142
    read radius
    result=`echo "(4 * $p) * $radius^2" |bc`
    zenity --info --text="$result"
    ;;


        cone)
    zenity --info --text="Surface Area Of Cone"
    p=3.142
    radius=`zenity --entry --text="Enter Radius of the cone"` 
    read radius
    
    length=`zenity --entry --text="Enter length of the cone"`
    read length
    result=`echo "($p * $radius * $length) + ($p * $radius^2)" |bc`
    zenity --info --text="$result"
    
    ;;


        cylinder)
    zenity --info --text="Surface Area Of Cylinder"
    radius=`zenity --entry --text="Enter Radius of the cylinder"`
    read radius
    
    height=`zenity --entry --text="Enter height of the cylinder"`
    read height
    
    p=3.142
    result=`echo "(2 * $p * $radius^2) + (2 * $p * $radius * $height)" |bc`
    zenity --info --text="$result"
    ;;

        exit)
        exit
        
        ;;
        esac


```i have added me full code and calculation in the choosen option.. please have a look and trll me what i am missing dat the form is not proceeding to ask for user input than just terminating...


thanxs man

---

### Post by kerry_s on 2010-04-15
try this 1, run the script in terminal to see errors, i didn't get any. i read the manpage for bc, so i think the math is right, but then again i do suck at math. :)

Edit:changed info to show the test run, not in the pics.

```

#!/bin/bash

sel=`zenity --height="300" --width="300" --list --title="Paint Math Pro" --column="Select calculation to perform" "Surface Area Of Sphere" "Surface Area Of Cone" "Surface Area Of Cylinder"`

if [ "$sel" == "Surface Area Of Sphere" ]; then
    radius=`zenity --entry --text="Enter Radius of the sphere"` 
    result=$(echo "4 * 3.142 * $radius^2" | bc -s)
    zenity --info --text="Surface Area Of Sphere $result"


elif [ "$sel" == "Surface Area Of Cone" ]; then
    radius=`zenity --entry --text="Enter Radius of the cone"`
    length=`zenity --entry --text="Enter Length of the cone"`
    result=$(echo "3.142 * $radius * $length + 3.142 * $radius^2" | bc -s)
    zenity --info --text="Surface Area Of Cone $result"

elif [ "$sel" == "Surface Area Of Cylinder" ]; then
    radius=`zenity --entry --text="Enter Radius of the cylinder"`
    height=`zenity --entry --text="Enter Height of the cylinder"`
    result=$(echo "2 * 3.142 * $radius^2 + 2 * 3.142 * $radius * $height" | bc -s)
    zenity --info --text="Surface Area Of Cylinder $result"
    
fi
exit 0


```

the rest of pics in next post.

---

### Post by kerry_s on 2010-04-15
rest of pics.

---

### Post by skula on 2010-04-16
Kerry,
 
 thank you very much...it is working perfectly now....
 
 i still got final soluton needed....
 
 i  am thinkin of a situaon where after an option is selected to be performed and the action is performed for the selected menu option.... it woulod return back to the main menu zenity option so anoda task can be performed instead of having to run de script again each time to pergorm anoda task..
 
 
 ty for all ur help

---

### Post by kerry_s on 2010-04-16
> **skula said:**
> Kerry,
 
 thank you very much...it is working perfectly now....
 
 i still got final soluton needed....
 
 i  am thinkin of a situaon where after an option is selected to be performed and the action is performed for the selected menu option.... it woulod return back to the main menu zenity option so anoda task can be performed instead of having to run de script again each time to pergorm anoda task..
 
 
 ty for all ur help


i think i can work that in, say a simple question like "would you like to perform another task" with a yes/no.

i just got up so your going to have to wait till i have some coffee & a cig.

---

### Post by skula on 2010-04-16
ok ty

---

### Post by kerry_s on 2010-04-16
okay i think i got it, you'll need to change "test.sh" to name your using for the script on all 3 parts i'll mark it **bold**.

```

#!/bin/bash

sel=`zenity --height="300" --width="300" --list --title="Paint Math Pro" --column="Select calculation to perform" "Surface Area Of Sphere" "Surface Area Of Cone" "Surface Area Of Cylinder"`

if [ "$sel" == "Surface Area Of Sphere" ]; then
    radius=`zenity --entry --text="Enter Radius of the sphere"` 
    result=$(echo "4 * 3.142 * $radius^2" | bc -s)
    zenity --info --text="Surface Area Of Sphere $result"
    zenity --question --text="Perform another task\?"
    if [ "$?" == "0" ]; then
      **test.sh**
     else
      exit 0
    fi

elif [ "$sel" == "Surface Area Of Cone" ]; then
    radius=`zenity --entry --text="Enter Radius of the cone"`
    length=`zenity --entry --text="Enter Length of the cone"`
    result=$(echo "3.142 * $radius * $length + 3.142 * $radius^2" | bc -s)
    zenity --info --text="Surface Area Of Cone $result"
    zenity --question --text="Perform another task\?"
    if [ "$?" == "0" ]; then
      **test.sh**
     else
      exit 0
    fi

elif [ "$sel" == "Surface Area Of Cylinder" ]; then
    radius=`zenity --entry --text="Enter Radius of the cylinder"`
    height=`zenity --entry --text="Enter Height of the cylinder"`
    result=$(echo "2 * 3.142 * $radius^2 + 2 * 3.142 * $radius * $height" | bc -s)
    zenity --info --text="Surface Area Of Cylinder $result"
    zenity --question --text="Perform another task\?"
    if [ "$?" == "0" ]; then
      **test.sh**
     else
      exit 0
    fi

fi
exit 0


```

---

### Post by skula on 2010-04-16
ok kelrry thanks for doing a good work on me.. no u are making me to understand and play with bash

this is my progress so far 

```
#!/bin/bash
#programmed by skula

option=`zenity --height="300" --width="300" --list --title="Paint Math Pro" --column="Select calculation to perform" "Surface Area Of Sphere" "Surface Area Of Cone" "Surface Area Of Cylinder" "Exit"`


if [ "$option" == "Surface Area Of Sphere" ]; 
then
p=3.142
    radius=`zenity --entry --text="Enter Radius of the sphere"` 
    
    result=$(echo "4 * $p * $radius^2" | bc)
    zenity --info --text="Surface Area Of Sphere $result"
    
    zenity --question --text="Do You Want to Perform Another Calculation?"
    
         if [ "$?" == "0" ];
           then
           paintmathpro
           else
           exit 0
          fi


elif [ "$option" == "Surface Area Of Cone" ]; 
then
    p=3.142
    radius=`zenity --entry --text="Enter Radius of the cone"`
    length=`zenity --entry --text="Enter Length of the cone"`
    result=$(echo "$p * $radius * $length + 3.142 * $radius^2" | bc)
    zenity --info --text="Surface Area Of Cone $result"
    zenity --question --text="Do You Want to Perform Another Calculation?"
    
         if [ "$?" == "0" ];
           then
           paintmathpro
           else
           exit 0
          fi

elif [ "$option" == "Surface Area Of Cylinder" ]; then
     p=3.142
    radius=`zenity --entry --text="Enter Radius of the cylinder"`
    height=`zenity --entry --text="Enter Height of the cylinder"`
    result=$(echo "2 * $p * $radius^2 + 2 * $p * $radius * $height" | bc)
    zenity --info --text="Surface Area Of Cylinder $result"
    zenity --question --text="Do You Want to Perform Another Calculation?"
    
         if [ "$?" == "0" ];
           then
           paintmathpro
           else
           exit 0
          fi
    
elif [ "$option" == "Exit" ];
    then
    zenity --question --text="Are You Sure You Want To End This Program?"
    if [ "$?" == "0" ];
           then
    zenity --info --text="Exiting Program Now"
           elif [ "$?" != "0" ];
           then
           paintmathpro
           
           else
           exit 0
          fi
          
    
    exit 0
    
fi
exit 0
```

i have even added a parameter for the exit command such that if a user choose to exit a confirmation on exit is displayed and if the user changes his mind that the exit was a mistake and clicks on cancel, the user is taken back to the men menu...


now what i want to achieve now is to add some validation on the user entered input in the textbox such that if the users  does not enter any value and if the user enters anything other than a numeric value
an error is displayed prompting the user that a numeric input is accepted only  and then if the user clicks the ok on the error zenity button user is taken back to the intial text screen to re enter a number value....


i know this is getting complex now but my mind is wondering and lookin forward to doing more...


thank u for ur time.. well appreciated

---

### Post by kerry_s on 2010-04-16
> now what i want to achieve now is to add some validation on the user entered input in the textbox such that if the users does not enter any value and if the user enters anything other than a numeric value
an error is displayed prompting the user that a numeric input is accepted only and then if the user clicks the ok on the error zenity button user is taken back to the intial text screen to re enter a number value....


i know this is getting complex now but my mind is wondering and lookin forward to doing more...

sounds do-able, can probably use like a " grep "^[0-9]" " to test the output from that zenity command, the error & running just that command again, you'll probably need to switch to a while loop.

anyways, i'll look into it later. i just spent 4hours in traffic & got a headache thats killin me.

---

### Post by skula on 2010-04-17
ok pal..

thanxfor all the asistance... do have a rest  ,.. ni think that would make u feel better

---

