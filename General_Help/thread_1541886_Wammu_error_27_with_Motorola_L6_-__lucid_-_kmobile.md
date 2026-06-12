---
title: "Wammu error 27 with Motorola L6 -  lucid - kmobiletools"
date: 2010-07-29
forum: General Help
---

### Post by anotherone33 on 2010-07-29
hi all.

I tried :
wammu + gammu (all) in ubuntu lucid x64  . motorola l6
And I succeed in have working it, getting contacts not completely but sufficiently. 
[Getting messages working well and backup working.]

Because:
kmobiletools work, but less easy. Messages save one by one, not able to configure contact sync (kontact, k... so on kde tools), so ... copying then by hand ?

The error in wammu when getting contacts:
GSM_GetNextMemory failed with error UNKNOWN[27]:Unknown Error.

How:
I observed that error 27 come when first attempt to sync contacts 
> Get Contacts(all)  
[sorry may be english is different I try to figure out from my language...] 
and I observed debug log. It seems the command "AT+MPBR= gets the wrong number for example it gets the first number in SM or SE may be 501 and then the next it gets wrong was 1002 !(doesn't exist, I remember kmobiletools sm-xxx ..) and error message windows  want an 'ok' for any error and the message is citing 502 and not 1002 !!!!

**So may be in some point in the procedure there is an addition in excess.** Or some wrong reference.

Story:
When I got my tries (yes I tried little changes) less frequent update in configurations, not 30000 default but 3000. And log window.  Fortune I could see one right getting of contacts in log window (with names and numbers ! yeah)
And then I tried to reproduce again... so here to tell you.

By the way coming from this first [http://ubuntuforums.org/showthread.php?t=635932](http://ubuntuforums.org/showthread.php?t=635932) closed.  And the manual for gsm commands here [https://docs.symbol.com/manuals/5747402a.pdf](https://docs.symbol.com/manuals/5747402a.pdf)   G18 GSM/GPRS Modem AT Command Set.

So when first try going wrong in getting contacts don't discourage !
I navigate and clicked on folder contacts and contacts. Then stopping on one contact of mobile and getting contacts mobile. Moving some keys on my phone  (stop, navigate ....), moving window with working get and again getting contacts without errors.
Similar for sim, stopping on one contact and getting only sim contacts and hitting some keys on phone and getting them again.
I have the log, but inside are my contact ... sorry, not for all the world.

The getting seems work well the first time only for some numbers,  sm-501  and me-1 me-2 me-3 .

Examining the log

```
Thu 2010/07/29 23:39:49: 0A |4FO|4BK|0D |0A                                              .OK..           
Thu 2010/07/29 23:39:49: Memory status received
Thu 2010/07/29 23:39:49: Parsing +CPBS: "SM",67,250 with +CPBS: @s, @i, @i
Thu 2010/07/29 23:39:49: Grabbed string from reply: "SM" (parsed 4 bytes)
Thu 2010/07/29 23:39:49: Parsed generic string "SM"
Thu 2010/07/29 23:39:49: Generic string decoded as "SM"
Thu 2010/07/29 23:39:49: Parsed int 67
Thu 2010/07/29 23:39:49: Parsed int 250
Thu 2010/07/29 23:39:49: Getting memory information
Thu 2010/07/29 23:39:49: Already in mode 2
Thu 2010/07/29 23:39:49: SENDING frametype 0x00/length 0x0A/10
Thu 2010/07/29 23:39:49: 41A|54T|2B+|43C|50P|42B|52R|3D=|3F?|0D                          AT+CPBR=?.      
Thu 2010/07/29 23:39:49: 1 "AT+CPBR=?"
Thu 2010/07/29 23:39:49: 2 "+CPBR: (501-750),40,15"
Thu 2010/07/29 23:39:49: 3 "OK"
Thu 2010/07/29 23:39:49: RECEIVED frametype 0x00/length 0x2A/42
Thu 2010/07/29 23:39:49: 41A|54T|2B+|43C|50P|42B|52R|3D=|3F?|0D |0D |0A |2B+|43C|50P|42B AT+CPBR=?...+CPB
Thu 2010/07/29 23:39:49: 52R|3A:|20 |28(|355|300|311|2D-|377|355|300|29)|2C,|344|300|2C, R: (501-750),40,
Thu 2010/07/29 23:39:49: 311|355|0D |0A |0D |0A |4FO|4BK|0D |0A                          15....OK..      
Thu 2010/07/29 23:39:49: Memory info received
Thu 2010/07/29 23:39:49: Parsing +CPBR: (501-750),40,15 with +CPBR: (@i-@i), @i, @i
Thu 2010/07/29 23:39:49: Parsed int 501
Thu 2010/07/29 23:39:49: Parsed int 750
Thu 2010/07/29 23:39:49: Parsed int 40
Thu 2010/07/29 23:39:49: Parsed int 15
Thu 2010/07/29 23:39:49: Leaving GSM_GetMemoryStatus
Thu 2010/07/29 23:39:49: Entering GSM_GetNextMemory
Thu 2010/07/29 23:39:49: Starting reading!
Thu 2010/07/29 23:39:49: Location = -1, Memory type = SM
Thu 2010/07/29 23:39:49: Getting phonebook entry
Thu 2010/07/29 23:39:49: Nothing known about AT+MPBR=501
 command, using current mode
Thu 2010/07/29 23:39:49: SENDING frametype 0x00/length 0x0C/12
Thu 2010/07/29 23:39:49: 41A|54T|2B+|4DM|50P|42B|52R|3D=|355|300|311|0D                  AT+MPBR=501.    
Thu 2010/07/29 23:39:49: 1 "AT+MPBR=501"
Thu 2010/07/29 23:39:49: 2 "+MPBR: 501,"+393288274221",145,004D0061006400640079,8,0,255,0,0,1,255,255,0,,0,0,,,,,,,,"","""
Thu 2010/07/29 23:39:49: 3 "OK"
Thu 2010/07/29 23:39:49: RECEIVED frametype 0x00/length 0x73/115
Thu 2010/07/29 23:39:49: 41A|54T|2B+|4DM|50P|42B|52R|3D=|355|300|311|0D |0D |0A |2B+|4DM AT+MPBR=501...+M
Thu 2010/07/29 23:39:49: 50P|42B|52R|3A:|20 |355|300|311|2C,|22"|2B+|333|399|333|322|388 PBR: 501,"+39328
Thu 2010/07/29 23:39:49: 388|322|377|344|322|322|311|22"|2C,|311|344|355|2C,|300|300|344 8274221",145,004
Thu 2010/07/29 23:39:49: 44D|300|300|366|311|300|300|366|344|300|300|366|344|300|300|377 D006100640064007
Thu 2010/07/29 23:39:49: 399|2C,|388|2C,|300|2C,|322|355|355|2C,|300|2C,|300|2C,|311|2C, 9,8,0,255,0,0,1,
Thu 2010/07/29 23:39:49: 322|355|355|2C,|322|355|355|2C,|300|2C,|2C,|300|2C,|300|2C,|2C, 255,255,0,,0,0,,
Thu 2010/07/29 23:39:49: 2C,|2C,|2C,|2C,|2C,|2C,|22"|22"|2C,|22"|22"|0D |0A |0D |0A |4FO ,,,,,,"",""....O
Thu 2010/07/29 23:39:49: 4BK|0D |0A                                                      K..             
Thu 2010/07/29 23:39:49: Phonebook entry received
Thu 2010/07/29 23:39:49: Parsing +MPBR: 501,"+393288274221",145,004D0061006400640079,8,0,255,0,0,1,255,255,0,,0,0,,,,,,,,"","" with +MPBR: @i, @p, @i, @s, @i, @0
Thu 2010/07/29 23:39:49: Parsed int 501
Thu 2010/07/29 23:39:49: Grabbed string from reply: "+39xxxxxxxxxx" (parsed 15 bytes)
Thu 2010/07/29 23:39:49: Parsed phone string "+39xxxxxxxxxx"
Thu 2010/07/29 23:39:49: Phone string decoded as "+39xxxxxxxxxx"
Thu 2010/07/29 23:39:49: Parsed int 145
Thu 2010/07/29 23:39:49: Grabbed string from reply: "004D0061006400640079" (parsed 20 bytes)
Thu 2010/07/29 23:39:49: Parsed generic string "004D0061006400640079"
Thu 2010/07/29 23:39:49: Generic string decoded as "xxxxx"
Thu 2010/07/29 23:39:49: Parsed int 8
Thu 2010/07/29 23:39:49: Leaving GSM_GetNextMemory
Thu 2010/07/29 23:39:49: Entering GSM_GetNextMemory
Thu 2010/07/29 23:39:49: Location = 501, Memory type = SM
Thu 2010/07/29 23:39:49: Getting phonebook entry
Thu 2010/07/29 23:39:49: Nothing known about AT+MPBR=1002
 command, using current mode
Thu 2010/07/29 23:39:49: SENDING frametype 0x00/length 0x0D/13
Thu 2010/07/29 23:39:49: 41A|54T|2B+|4DM|50P|42B|52R|3D=|311|300|300|322|0D              AT+MPBR=1002.   
Thu 2010/07/29 23:39:49: 1 "AT+MPBR=1002"
Thu 2010/07/29 23:39:49: 2 "ERROR"
Thu 2010/07/29 23:39:49: RECEIVED frametype 0x00/length 0x16/22
Thu 2010/07/29 23:39:49: 41A|54T|2B+|4DM|50P|42B|52R|3D=|311|300|300|322|0D |0D |0A |45E AT+MPBR=1002...E
Thu 2010/07/29 23:39:49: 52R|52R|4FO|52R|0D |0A                                          RROR..          
Thu 2010/07/29 23:39:49: GSM_GetNextMemory failed with error UNKNOWN[27]: Errore sconosciuto.
Thu 2010/07/29 23:39:49: Leaving GSM_GetNextMemory
```

The time it goes not with error:
```

Thu 2010/07/29 23:41:38: SENDING frametype 0x00/length 0x0C/12
Thu 2010/07/29 23:41:38: 41A|54T|2B+|4DM|50P|42B|52R|3D=|344|399|399|0D                  AT+MPBR=499.    
Thu 2010/07/29 23:41:38: 1 "AT+MPBR=499"
Thu 2010/07/29 23:41:38: 2 "OK"
Thu 2010/07/29 23:41:38: RECEIVED frametype 0x00/length 0x12/18
Thu 2010/07/29 23:41:38: 41A|54T|2B+|4DM|50P|42B|52R|3D=|344|399|399|0D |0D |0A |4FO|4BK AT+MPBR=499...OK
Thu 2010/07/29 23:41:38: 0D |0A                                                          ..              
Thu 2010/07/29 23:41:38: Phonebook entry received
Thu 2010/07/29 23:41:38: Getting phonebook entry
Thu 2010/07/29 23:41:38: Nothing known about AT+MPBR=500
 command, using current mode
Thu 2010/07/29 23:41:38: SENDING frametype 0x00/length 0x0C/12
Thu 2010/07/29 23:41:38: 41A|54T|2B+|4DM|50P|42B|52R|3D=|355|300|300|0D                  AT+MPBR=500.    
Thu 2010/07/29 23:41:38: 1 "AT+MPBR=500"
Thu 2010/07/29 23:41:38: 2 "OK"
Thu 2010/07/29 23:41:38: RECEIVED frametype 0x00/length 0x12/18
Thu 2010/07/29 23:41:38: 41A|54T|2B+|4DM|50P|42B|52R|3D=|355|300|300|0D |0D |0A |4FO|4BK AT+MPBR=500...OK
Thu 2010/07/29 23:41:38: 0D |0A                                                          ..              
Thu 2010/07/29 23:41:38: Phonebook entry received
Thu 2010/07/29 23:41:38: Getting phonebook entry
Thu 2010/07/29 23:41:38: Nothing known about AT+MPBR=501
 command, using current mode
Thu 2010/07/29 23:41:38: SENDING frametype 0x00/length 0x0C/12
Thu 2010/07/29 23:41:38: 41A|54T|2B+|4DM|50P|42B|52R|3D=|355|300|311|0D                  AT+MPBR=501.    
Thu 2010/07/29 23:41:38: 1 "AT+MPBR=501"
Thu 2010/07/29 23:41:38: 2 "+MPBR: 501,"+393288274221",145,004D0061006400640079,8,0,255,0,1,1,255,255,0,,0,0,,,,,,,,"","""
Thu 2010/07/29 23:41:38: 3 "OK"
Thu 2010/07/29 23:41:38: RECEIVED frametype 0x00/length 0x73/115
Thu 2010/07/29 23:41:38: 41A|54T|2B+|4DM|50P|42B|52R|3D=|355|300|311|0D |0D |0A |2B+|4DM AT+MPBR=501...+M
Thu 2010/07/29 23:41:38: 50P|42B|52R|3A:|20 |355|300|311|2C,|22"|2B+|333|399|333|322|388 PBR: 501,"+39328
Thu 2010/07/29 23:41:38: 388|322|377|344|322|322|311|22"|2C,|311|344|355|2C,|300|300|344 8274221",145,004
Thu 2010/07/29 23:41:38: 44D|300|300|366|311|300|300|366|344|300|300|366|344|300|300|377 D006100640064007
Thu 2010/07/29 23:41:38: 399|2C,|388|2C,|300|2C,|322|355|355|2C,|300|2C,|311|2C,|311|2C, 9,8,0,255,0,1,1,
Thu 2010/07/29 23:41:38: 322|355|355|2C,|322|355|355|2C,|300|2C,|2C,|300|2C,|300|2C,|2C, 255,255,0,,0,0,,
Thu 2010/07/29 23:41:38: 2C,|2C,|2C,|2C,|2C,|2C,|22"|22"|2C,|22"|22"|0D |0A |0D |0A |4FO ,,,,,,"",""....O
Thu 2010/07/29 23:41:38: 4BK|0D |0A                                                      K..             
Thu 2010/07/29 23:41:38: Phonebook entry received
Thu 2010/07/29 23:41:38: Parsing +MPBR: 501,"+393288274221",145,004D0061006400640079,8,0,255,0,1,1,255,255,0,,0,0,,,,,,,,"","" with +MPBR: @i, @p, @i, @s, @i, @0
Thu 2010/07/29 23:41:38: Parsed int 501
Thu 2010/07/29 23:41:38: Grabbed string from reply: "+39xxxxxxxxxx" (parsed 15 bytes)
Thu 2010/07/29 23:41:38: Parsed phone string "+39xxxxxxxxxx"
Thu 2010/07/29 23:41:38: Phone string decoded as "+39xxxxxxxxxx"
Thu 2010/07/29 23:41:38: Parsed int 145
Thu 2010/07/29 23:41:38: Grabbed string from reply: "004D0061006400640079" (parsed 20 bytes)
Thu 2010/07/29 23:41:38: Parsed generic string "004D0061006400640079"
Thu 2010/07/29 23:41:38: Generic string decoded as "xxxxx"
Thu 2010/07/29 23:41:38: Parsed int 8
Thu 2010/07/29 23:41:38: Leaving GSM_GetNextMemory
Thu 2010/07/29 23:41:38: Entering GSM_GetSignalQuality
Thu 2010/07/29 23:41:38: Getting signal quality info
Thu 2010/07/29 23:41:38: Switching to mode 0
Thu 2010/07/29 23:41:38: SENDING frametype 0x00/length 0x0A/10
Thu 2010/07/29 23:41:38: 41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D                          AT+MODE=0.      
Thu 2010/07/29 23:41:38: 1 "AT+MODE=0"
Thu 2010/07/29 23:41:38: 2 "OK"
Thu 2010/07/29 23:41:38: RECEIVED frametype 0x00/length 0x10/16
Thu 2010/07/29 23:41:38: 41A|54T|2B+|4DM|4FO|44D|45E|3D=|300|0D |0D |0A |4FO|4BK|0D |0A  AT+MODE=0...OK..
Thu 2010/07/29 23:41:38: SENDING frametype 0x00/length 0x07/7
Thu 2010/07/29 23:41:38: 41A|54T|2B+|43C|53S|51Q|0D                                      AT+CSQ.         
Thu 2010/07/29 23:41:39: 1 "AT+CSQ"
Thu 2010/07/29 23:41:39: 2 "+CSQ: 27,99"
Thu 2010/07/29 23:41:39: 3 "OK"
Thu 2010/07/29 23:41:39: RECEIVED frametype 0x00/length 0x1C/28
Thu 2010/07/29 23:41:39: 41A|54T|2B+|43C|53S|51Q|0D |0D |0A |2B+|43C|53S|51Q|3A:|20 |322 AT+CSQ...+CSQ: 2
Thu 2010/07/29 23:41:39: 377|2C,|399|399|0D |0A |0D |0A |4FO|4BK|0D |0A                  7,99....OK..    
Thu 2010/07/29 23:41:39: Signal quality info received
Thu 2010/07/29 23:41:39: Parsing +CSQ: 27,99 with +CSQ: @i, @i
Thu 2010/07/29 23:41:39: Parsed int 27
Thu 2010/07/29 23:41:39: Parsed int 99
Thu 2010/07/29 23:41:39: Leaving GSM_GetSignalQuality
Thu 2010/07/29 23:41:39: Entering GSM_GetBatteryCharge
Thu 2010/07/29 23:41:39: Getting battery charge
Thu 2010/07/29 23:41:39: Switching to mode 2
Thu 2010/07/29 23:41:39: SENDING frametype 0x00/length 0x0A/10
Thu 2010/07/29 23:41:39: 41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|0D                          AT+MODE=2.      
Thu 2010/07/29 23:41:39: 1 "AT+MODE=2"
Thu 2010/07/29 23:41:39: 2 "OK"
Thu 2010/07/29 23:41:39: RECEIVED frametype 0x00/length 0x10/16
Thu 2010/07/29 23:41:39: 41A|54T|2B+|4DM|4FO|44D|45E|3D=|322|0D |0D |0A |4FO|4BK|0D |0A  AT+MODE=2...OK..
Thu 2010/07/29 23:41:39: Waiting for banner...
Thu 2010/07/29 23:41:39: 1 "+MBAN: Copyright 2000-2002 Motorola, Inc."
Thu 2010/07/29 23:41:39: RECEIVED frametype 0x00/length 0x2B/43
Thu 2010/07/29 23:41:39: 2B+|4DM|42B|41A|4EN|3A:|20 |43C|6Fo|70p|79y|72r|69i|67g|68h|74t +MBAN: Copyright
Thu 2010/07/29 23:41:39: 20 |322|300|300|300|2D-|322|300|300|322|20 |4DM|6Fo|74t|6Fo|72r  2000-2002 Motor
Thu 2010/07/29 23:41:39: 6Fo|6Cl|61a|2C,|20 |49I|6En|63c|2E.|0D |0A                      ola, Inc...     
Thu 2010/07/29 23:41:39: Already in mode 2
Thu 2010/07/29 23:41:39: SENDING frametype 0x00/length 0x0F/15
Thu 2010/07/29 23:41:39: 41A|54T|2B+|43C|53S|43C|53S|3D=|22"|55U|43C|53S|322|22"|0D      AT+CSCS="UCS2". 
Thu 2010/07/29 23:41:39: 1 "AT+CSCS="UCS2""
Thu 2010/07/29 23:41:39: 2 "OK"
Thu 2010/07/29 23:41:39: RECEIVED frametype 0x00/length 0x15/21
Thu 2010/07/29 23:41:39: 41A|54T|2B+|43C|53S|43C|53S|3D=|22"|55U|43C|53S|322|22"|0D |0D  AT+CSCS="UCS2"..
Thu 2010/07/29 23:41:39: 0A |4FO|4BK|0D |0A                                              .OK..           
Thu 2010/07/29 23:41:39: Already in mode 2
Thu 2010/07/29 23:41:39: SENDING frametype 0x00/length 0x09/9
Thu 2010/07/29 23:41:39: 41A|54T|2B+|43C|53S|43C|53S|3F?|0D                              AT+CSCS?.       
Thu 2010/07/29 23:41:39: 1 "AT+CSCS?"
Thu 2010/07/29 23:41:39: 2 "+CSCS: "UCS2""
Thu 2010/07/29 23:41:39: 3 "OK"
Thu 2010/07/29 23:41:39: RECEIVED frametype 0x00/length 0x20/32
Thu 2010/07/29 23:41:39: 41A|54T|2B+|43C|53S|43C|53S|3F?|0D |0D |0A |2B+|43C|53S|43C|53S AT+CSCS?...+CSCS
Thu 2010/07/29 23:41:39: 3A:|20 |22"|55U|43C|53S|322|22"|0D |0A |0D |0A |4FO|4BK|0D |0A  : "UCS2"....OK..
Thu 2010/07/29 23:41:39: SENDING frametype 0x00/length 0x07/7
Thu 2010/07/29 23:41:39: 41A|54T|2B+|43C|42B|43C|0D                                      AT+CBC.         
Thu 2010/07/29 23:41:39: 1 "AT+CBC"
Thu 2010/07/29 23:41:39: 2 "+CBC: 1,90"
Thu 2010/07/29 23:41:39: 3 "OK"
Thu 2010/07/29 23:41:39: RECEIVED frametype 0x00/length 0x1B/27
Thu 2010/07/29 23:41:39: 41A|54T|2B+|43C|42B|43C|0D |0D |0A |2B+|43C|42B|43C|3A:|20 |311 AT+CBC...+CBC: 1
Thu 2010/07/29 23:41:39: 2C,|399|300|0D |0A |0D |0A |4FO|4BK|0D |0A                      ,90....OK..     
Thu 2010/07/29 23:41:39: Battery level received
Thu 2010/07/29 23:41:39: Parsing +CBC: 1,90 with +CBC: @i, @i
Thu 2010/07/29 23:41:39: Parsed int 1
Thu 2010/07/29 23:41:39: Parsed int 90
Thu 2010/07/29 23:41:39: Leaving GSM_GetBatteryCharge
Thu 2010/07/29 23:41:39: Entering GSM_GetDateTime
Thu 2010/07/29 23:41:39: Getting date & time
Thu 2010/07/29 23:41:39: Already in mode 2
Thu 2010/07/29 23:41:39: SENDING frametype 0x00/length 0x09/9
Thu 2010/07/29 23:41:39: 41A|54T|2B+|43C|43C|4CL|4BK|3F?|0D                              AT+CCLK?.       
Thu 2010/07/29 23:41:39: 1 "AT+CCLK?"
Thu 2010/07/29 23:41:39: 2 "+CCLK: "10/07/29,23:41:39+00""
Thu 2010/07/29 23:41:39: 3 "OK"
Thu 2010/07/29 23:41:39: RECEIVED frametype 0x00/length 0x30/48
Thu 2010/07/29 23:41:39: 41A|54T|2B+|43C|43C|4CL|4BK|3F?|0D |0D |0A |2B+|43C|43C|4CL|4BK AT+CCLK?...+CCLK
Thu 2010/07/29 23:41:39: 3A:|20 |22"|311|300|2F/|300|377|2F/|322|399|2C,|322|333|3A:|344 : "10/07/29,23:4
Thu 2010/07/29 23:41:39: 311|3A:|333|399|2B+|300|300|22"|0D |0A |0D |0A |4FO|4BK|0D |0A  1:39+00"....OK..
Thu 2010/07/29 23:41:39: Parsing +CCLK: "10/07/29,23:41:39+00" with +CCLK: @d
Thu 2010/07/29 23:41:39: Grabbed string from reply: "10/07/29,23:41:39+00" (parsed 22 bytes)
Thu 2010/07/29 23:41:39: Parsed string for date "10/07/29,23:41:39+00"
Thu 2010/07/29 23:41:39: Leaving GSM_GetDateTime
Thu 2010/07/29 23:41:39: Entering GSM_GetNextMemory
Thu 2010/07/29 23:41:39: Location = 501, Memory type = ME
Thu 2010/07/29 23:41:39: Getting phonebook entry
Thu 2010/07/29 23:41:39: Nothing known about AT+MPBR=502
 command, using current mode
Thu 2010/07/29 23:41:39: SENDING frametype 0x00/length 0x0C/12
Thu 2010/07/29 23:41:39: 41A|54T|2B+|4DM|50P|42B|52R|3D=|355|300|322|0D                  AT+MPBR=502.    
Thu 2010/07/29 23:41:39: 1 "AT+MPBR=502"
Thu 2010/07/29 23:41:39: 2 "+MPBR: 502,"340760514",129,0043006C0061007500640069006100200041006D00610074,8,0,255,0,1,1,255,255,0,,0,0,,,,,,,,"","""
Thu 2010/07/29 23:41:39: 3 "OK"
Thu 2010/07/29 23:41:39: RECEIVED frametype 0x00/length 0x8B/139
Thu 2010/07/29 23:41:39: 41A|54T|2B+|4DM|50P|42B|52R|3D=|355|300|322|0D |0D |0A |2B+|4DM AT+MPBR=502...+M
Thu 2010/07/29 23:41:39: 50P|42B|52R|3A:|20 |355|300|322|2C,|22"|333|344|300|377|366|300 PBR: 502,"340760
Thu 2010/07/29 23:41:39: 355|311|344|22"|2C,|311|322|399|2C,|300|300|344|333|300|300|366 514",129,0043006
Thu 2010/07/29 23:41:39: 43C|300|300|366|311|300|300|377|355|300|300|366|344|300|300|366 C006100750064006
Thu 2010/07/29 23:41:39: 399|300|300|366|311|300|300|322|300|300|300|344|311|300|300|366 9006100200041006
Thu 2010/07/29 23:41:39: 44D|300|300|366|311|300|300|377|344|2C,|388|2C,|300|2C,|322|355 D00610074,8,0,25
Thu 2010/07/29 23:41:39: 355|2C,|300|2C,|311|2C,|311|2C,|322|355|355|2C,|322|355|355|2C, 5,0,1,1,255,255,
Thu 2010/07/29 23:41:39: 300|2C,|2C,|300|2C,|300|2C,|2C,|2C,|2C,|2C,|2C,|2C,|2C,|22"|22" 0,,0,0,,,,,,,,""
Thu 2010/07/29 23:41:39: 2C,|22"|22"|0D |0A |0D |0A |4FO|4BK|0D |0A                      ,""....OK..     
Thu 2010/07/29 23:41:39: Phonebook entry received
Thu 2010/07/29 23:41:39: Parsing +MPBR: 502,"340760514",129,0043006C0061007500640069006100200041006D00610074,8,0,255,0,1,1,255,255,0,,0,0,,,,,,,,"","" with +MPBR: @i, @p, @i, @s, @i, @0
Thu 2010/07/29 23:41:39: Parsed int 502

```

Every time you disconnect, the first get contacts gets error. 
The second ....
I don't know if need  but if so ... navig + phone stop on phone (only a moving on phone) then get the freezed window and move a little.
May be happen ... suddendly go well getting working and getting phone contacts.

I examine phone contacts se and sm are duplicates, on kmobiletools there are more types AD, ME, MC, DC, MT, ON, QD, RC, SM ...

In wammy SM e ME and the same, may be duplicating or wrong ?
In kmt me-1 2 3 are duplicated in mt-1 2 3 and there are not sm-1 2 3 (that we have wrongly in wammy). Then ME- stops in kmt in wammy are wrong duplicating from 501 to 566 the SM (SM- 501 to 567 that are present in kmt). 

Hoping helps.

---

