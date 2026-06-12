---
title: "c++ valid date help"
date: 2011-03-12
forum: General Help
---

### Post by gabriel8a2002 on 2011-03-12
what is wrong with my code =(
  when calling datevalidation(2,29,2011) returns true while it supposed to be false

/*
 *Objective:  to find out if the date is a leapyear or not
 * Input:  the month, day, and year
 * Output:  True if it is leapyear, otherwise false
 */
bool isleapyear(unsigned short year){
	bool leapyear;
    if(year%400==0){
        leapyear=true;
    }
    else if(year%100==0){
        leapyear=false;
    }
    else if(year%4==0){
        leapyear=true;
    }
    else{
        leapyear=false;
    }
    return leapyear;
}
/*
 *Objective:  to validate if the date given is a valid date
 * Input:  the month, day, and year
 * Output:  true if its a valid date, false otherwise
 */
bool datevalidation(unsigned short usermonth, unsigned short userday, unsigned short useryear){
	//bool validation=false;
        if(usermonth>0&&usermonth<=12){
            if(usermonth==1||usermonth==3||usermonth==5
            ||usermonth==7||usermonth==8||usermonth==10||usermonth==12)
            {
                if(userday>0&&userday<=31){
                    return true;
                }
            return false;
            }
            else if(usermonth=4||usermonth==6||usermonth==9||usermonth==11){
                if(userday>0&&userday<=30){
                    return true;
                }
            return false;
            }
            else if(usermonth==2)
            {
                if(isleapyear(useryear)==true){
                    if(userday<=29&&userday>0){
                        return true;
                    }
                    return false;
                }
                else if(isleapyear(useryear)==false){
                    if(userday<=28&&userday>0){
                       return true;
                    }
                    return false;
                }
				return false;
            }
            return false;
		}
		return false;
}

---

### Post by gmargo on 2011-03-12
The "usermonth=4" is an assignment ('='), not a comparison ('==').
```

else if([COLOR=Red]usermonth=4[/COLOR]||usermonth==6||usermonth==9||usermonth==11){

```If you had used the "-Wall" option on gcc, you would have caught this.

And please use "[ code ]" ... "[ /code ]" tags around your code to preserve indentation.

---

