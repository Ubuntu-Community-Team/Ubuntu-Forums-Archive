---
title: "how to use serial port programming"
date: 2009-12-01
forum: General Help
---

### Post by athrun01 on 2009-12-01
I have code c program communnication with rs232 to CO2 sensor but it use for pic microcontroller. I want to convert code use on ubuntu. How to convert code

this code for pic microncontroller
```

//*** definition of the interface***
#use
rs232(baud=2400,XMIT=PIN_C6,rcv=PIN_C7,STREAM=CO,bits=7,parity=E,errors)
//***prepare request to the status flags***
#byte TXSTA = 0x98                      //from datasheet
#bit TRMT = TXSTA.1
#define wait_for_RS232() while(TRMT == 0)
void main(void) { // main function
boolean d = 1;
boolean e = 1;
char c1;
int i;
while (TRUE) {
    i = 0;
    e = 1;
    d = 1;
    delay_ms(100);
    fprintf(CO,":A00300050001A6\r\n"); //send request
    wait_for_RS232();                                 //wait for all data tob e sent
    if (kbhit(CO))
        {
          //***wait for the start of the strings to be received***
          while (e)
                 {
                  if(fgetc(CO) == ':') e=0;
                 delay_us(2);
                  }
           while (d)                     //running loop until LF
  {
           c1=fgetc(CO);                 //get characters from the interface
           str[i++]=c1;                 //store characters in the string
           if(c1 == 10) d = 0;         // 10 is the ASCII character for LF
         }
         auswerten();                  // Modulation
       }
  }
}
void auswerten()
{
  long co2long, co2r;
  int hilf;
   costring[0]='0';             //simulates hexadecimal number
   costring[1]='x';
   for(hilf=7;hilf<11;hilf++) //saves relevant values for the CO2 value
     {
     costring[hilf-5]=str[hilf];
     }
   costring[6]=0;               //end sign in the string gets set
   co2long = atol(costring); //changes string to long
   co2r=0.0000024169*(co2long*co2long*co2long); // callibration
   co2r=co2r+(0.001064478*(co2long*co2long));
   co2r=co2r+(1.5139504215*(co2long));
   i=0;                        //rest of the variable
   for(hilf=0;hilf<20;hilf++) str[hilf]=0;
}
```

data sheet 
[http://www.mediafire.com/?zjnwu4rogvx](http://www.mediafire.com/?zjnwu4rogvx)

---

