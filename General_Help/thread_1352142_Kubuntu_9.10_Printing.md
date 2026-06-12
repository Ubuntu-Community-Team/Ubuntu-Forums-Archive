---
title: "Kubuntu 9.10 Printing"
date: 2009-12-11
forum: General Help
---

### Post by gus_zernial on 2009-12-11
I'm running Kubuntu 9.10 with a custom 2.6.31.6 kernel. Problem is, I can't print PDF doscs thru Adobe Acrobat, and I can't print Thunderbird emails. I somehow have the impression Thunderbird converts emails to PDF format to print. CUPS error logs for failed print jobs are below.

I can print text files, Staroffice documents, Firefox/web pages and other stuff successfully. The problem is restricted to those cases described above.

Can someone give me an idea or link to fix?

Thx, Gus

--------------------------------PDF Job --------
D [11/Dec/2009:06:40:03 -0800] [Job 913] printer-state=3(idle)                                                             
D [11/Dec/2009:06:40:03 -0800] [Job 913] printer-state-message="Ready to print."                                              
D [11/Dec/2009:06:40:03 -0800] [Job 913] printer-state-reasons=none                                                           
E [11/Dec/2009:06:42:14 -0800] [Job 914] May not be a PDF file (continuing anyway)                                            
E [11/Dec/2009:06:42:14 -0800] [Job 914] PDF file is damaged - attempting to reconstruct xref table...                        
E [11/Dec/2009:06:42:14 -0800] [Job 914] Couldn't find trailer dictionary                                                     
E [11/Dec/2009:06:42:14 -0800] [Job 914] Couldn't read xref table                                                             
E [11/Dec/2009:06:42:19 -0800] [Job 914] Job stopped due to filter errors; please consult the error_log file for details.     
D [11/Dec/2009:06:42:19 -0800] [Job 914] The following messages were recorded from 06:42:14 to 06:42:19                       
D [11/Dec/2009:06:42:19 -0800] [Job 914] Adding start banner page "none".                                                     
D [11/Dec/2009:06:42:19 -0800] [Job 914] Queued on "E332n" by "rbroman".                                                      
D [11/Dec/2009:06:42:19 -0800] [Job 914] Auto-typing file...                                                                  
D [11/Dec/2009:06:42:19 -0800] [Job 914] Request file type is application/postscript.                                         
D [11/Dec/2009:06:42:19 -0800] [Job 914] File of type application/postscript queued by "rbroman".                             
D [11/Dec/2009:06:42:19 -0800] [Job 914] Adding end banner page "none".                                                       
D [11/Dec/2009:06:42:19 -0800] [Job 914] job-sheets=none,none                                                                 
D [11/Dec/2009:06:42:19 -0800] [Job 914] argv[0]="E332n"                                                                      
D [11/Dec/2009:06:42:19 -0800] [Job 914] argv[1]="914"                                                                        
D [11/Dec/2009:06:42:19 -0800] [Job 914] argv[2]="rbroman"                                                                    
D [11/Dec/2009:06:42:19 -0800] [Job 914] argv[3]="A9ROziUhuN"                                                                 
D [11/Dec/2009:06:42:19 -0800] [Job 914] argv[4]="1"                                                                          
D [11/Dec/2009:06:42:19 -0800] [Job 914] argv[5]="Collate finishings=3 Flash=InstalledF FormSubstitution=PrinterS InputSlot=Tray1 InputSources=Tray12 InstalledMemory=160Meg media=na_letter_8.5x11in MediaType=PrinterS number-up=1 PageRegion=Letter PageSize=Letter PictureGrade=PrinterS Resolution= SepPages=PrinterS SepSource=PrinterS TonerDarkness=PrinterS TonerSaver=PrinterS job-uuid=urn:uuid:c145a58a-03f0-3a71-6f60-1eacb9db43f6 job-originating-host-name=localhost"                                    
D [11/Dec/2009:06:42:19 -0800] [Job 914] argv[6]="/var/spool/cups/d00914-001"                                                 
D [11/Dec/2009:06:42:19 -0800] [Job 914] envp[0]="CUPS_CACHEDIR=/var/cache/cups"                                              
D [11/Dec/2009:06:42:19 -0800] [Job 914] envp[1]="CUPS_DATADIR=/usr/share/cups"                                               
D [11/Dec/2009:06:42:19 -0800] [Job 914] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"                                      
D [11/Dec/2009:06:42:19 -0800] [Job 914] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"                                        
D [11/Dec/2009:06:42:19 -0800] [Job 914] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"                                           
D [11/Dec/2009:06:42:19 -0800] [Job 914] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"                                               
D [11/Dec/2009:06:42:19 -0800] [Job 914] envp[6]="CUPS_SERVERROOT=/etc/cups"                                                  
D [11/Dec/2009:06:42:19 -0800] [Job 914] envp[7]="CUPS_STATEDIR=/var/run/cups"                                                
D [11/Dec/2009:06:42:19 -0800] [Job 914] envp[8]="HOME=/var/spool/cups/tmp"                                                   
D [11/Dec/2009:06:42:19 -0800] [Job 914] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"                 
D [11/Dec/2009:06:42:19 -0800] [Job 914] envp[10]="SERVER_ADMIN=root@jboat17"                                                 
D [11/Dec/2009:06:42:19 -0800] [Job 914] envp[11]="SOFTWARE=CUPS/1.4.1"                                                       
D [11/Dec/2009:06:42:19 -0800] [Job 914] envp[12]="TMPDIR=/var/spool/cups/tmp"                                                
D [11/Dec/2009:06:42:19 -0800] [Job 914] envp[13]="TZ=America/Los_Angeles"                                                    
D [11/Dec/2009:06:42:19 -0800] [Job 914] envp[14]="USER=root"                                                                 
D [11/Dec/2009:06:42:19 -0800] [Job 914] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"                                       
D [11/Dec/2009:06:42:19 -0800] [Job 914] envp[16]="CUPS_ENCRYPTION=IfRequested"                                               
D [11/Dec/2009:06:42:19 -0800] [Job 914] envp[17]="IPP_PORT=631"                                                              
D [11/Dec/2009:06:42:19 -0800] [Job 914] envp[18]="CHARSET=utf-8"                                                             
D [11/Dec/2009:06:42:19 -0800] [Job 914] envp[19]="LANG=en_US.UTF-8"                                                          
D [11/Dec/2009:06:42:19 -0800] [Job 914] envp[20]="PPD=/etc/cups/ppd/E332n.ppd"                                               
D [11/Dec/2009:06:42:19 -0800] [Job 914] envp[21]="RIP_MAX_CACHE=803910k"                                                     
D [11/Dec/2009:06:42:19 -0800] [Job 914] envp[22]="CONTENT_TYPE=application/postscript"                                       
D [11/Dec/2009:06:42:19 -0800] [Job 914] envp[23]="DEVICE_URI=socket://192.168.0.4:9100"                                      
D [11/Dec/2009:06:42:19 -0800] [Job 914] envp[24]="PRINTER_INFO=E332n"                                                        
D [11/Dec/2009:06:42:19 -0800] [Job 914] envp[25]="PRINTER_LOCATION=jboat17"                                                  
D [11/Dec/2009:06:42:19 -0800] [Job 914] envp[26]="PRINTER=E332n"                                                             
D [11/Dec/2009:06:42:19 -0800] [Job 914] envp[27]="CUPS_FILETYPE=document"                                                    
D [11/Dec/2009:06:42:19 -0800] [Job 914] envp[28]="FINAL_CONTENT_TYPE=application/vnd.cups-postscript"                        
D [11/Dec/2009:06:42:19 -0800] [Job 914] Started filter /usr/lib/cups/filter/pstopdf (PID 5437)                               
D [11/Dec/2009:06:42:19 -0800] [Job 914] Started filter /usr/lib/cups/filter/pdftopdf (PID 5438)                              
D [11/Dec/2009:06:42:19 -0800] [Job 914] Started filter /usr/lib/cups/filter/cpdftocps (PID 5439)                             
D [11/Dec/2009:06:42:19 -0800] [Job 914] Started backend /usr/lib/cups/backend/socket (PID 5440)                              
D [11/Dec/2009:06:42:19 -0800] [Job 914] pstopdf 6 args: 914 rbroman A9ROziUhuN 1 Collate finishings=3 Flash=InstalledF FormSubstitution=PrinterS InputSlot=Tray1 InputSources=Tray12 InstalledMemory=160Meg media=na_letter_8.5x11in MediaType=PrinterS number-up=1 PageRegion=Letter PageSize=Letter PictureGrade=PrinterS Resolution= SepPages=PrinterS SepSource=PrinterS TonerDarkness=PrinterS TonerSaver=PrinterS job-uuid=urn:uuid:c145a58a-03f0-3a71-6f60-1eacb9db43f6 job-originating-host-name=localhost /var/spool/cups/d00914-001                                                                                                        
D [11/Dec/2009:06:42:19 -0800] [Job 914] PPD: /etc/cups/ppd/E332n.ppd                                                         
D [11/Dec/2009:06:42:19 -0800] [Job 914] pdftops argv[5] = 914 rbroman A9ROziUhuN 1 Collate finishings=3 Flash=InstalledF FormSubstitution=PrinterS InputSlot=Tray1 InputSources=Tray12 InstalledMemory=160Meg media=na_letter_8.5x11in MediaType=PrinterS number-up=1 PageRegion=Letter PageSize=Letter PictureGrade=PrinterS Resolution= SepPages=PrinterS SepSource=PrinterS TonerDarkness=PrinterS TonerSaver=PrinterS job-uuid=urn:uuid:c145a58a-03f0-3a71-6f60-1eacb9db43f6 job-originating-host-name=localhost   
D [11/Dec/2009:06:42:19 -0800] [Job 914] PPD: /etc/cups/ppd/E332n.ppd                                                         
D [11/Dec/2009:06:42:19 -0800] [Job 914] /usr/bin/pdftops supports '-origpagesizes': yes                                      
D [11/Dec/2009:06:42:19 -0800] [Job 914] STATE: +connecting-to-device                                                         
D [11/Dec/2009:06:42:19 -0800] [Job 914] Looking up "192.168.0.4"...                                                          
D [11/Dec/2009:06:42:19 -0800] [Job 914] Connecting to 192.168.0.4:9100                                                       
D [11/Dec/2009:06:42:19 -0800] [Job 914] Connecting to printer...                                                             
D [11/Dec/2009:06:42:19 -0800] [Job 914] STATE: -connecting-to-device
D [11/Dec/2009:06:42:19 -0800] [Job 914] Connected to printer...
D [11/Dec/2009:06:42:19 -0800] [Job 914] Connected to 192.168.0.4:9100 (IPv4)...
D [11/Dec/2009:06:42:19 -0800] [Job 914] PostScript Level: 2
D [11/Dec/2009:06:42:19 -0800] [Job 914] Resolution:
D [11/Dec/2009:06:42:19 -0800] [Job 914] eval: 1: job-uuid=urn:uuid:c145a58a-03f0-3a71-6f60-1eacb9db43f6: not found
D [11/Dec/2009:06:42:19 -0800] [Job 914] Duplex: no
D [11/Dec/2009:06:42:19 -0800] [Job 914] Resolution:
D [11/Dec/2009:06:42:19 -0800] [Job 914] eval: 1: job-uuid=urn:uuid:c145a58a-03f0-3a71-6f60-1eacb9db43f6: not found
D [11/Dec/2009:06:42:19 -0800] [Job 914] hrDeviceDesc="Lexmark E332n 380GL63 141.C09 -- Part Number --"
D [11/Dec/2009:06:42:19 -0800] [Job 914] prtMarkerColorantValue.1.1 = "black"
D [11/Dec/2009:06:42:19 -0800] [Job 914] ATTR: marker-colors=#000000,none
D [11/Dec/2009:06:42:19 -0800] [Job 914] ATTR: marker-names="Black Toner","Photo Drum"
D [11/Dec/2009:06:42:19 -0800] [Job 914] ATTR: marker-types=toner,opc
D [11/Dec/2009:06:42:19 -0800] [Job 914] ATTR: marker-levels=40,0
D [11/Dec/2009:06:42:19 -0800] [Job 914] STATE: -media-low-report
D [11/Dec/2009:06:42:19 -0800] [Job 914] STATE: -media-empty-warning
D [11/Dec/2009:06:42:19 -0800] [Job 914] STATE: -toner-low-report
D [11/Dec/2009:06:42:19 -0800] [Job 914] STATE: -toner-empty-warning
D [11/Dec/2009:06:42:19 -0800] [Job 914] STATE: -door-open-report
D [11/Dec/2009:06:42:19 -0800] [Job 914] STATE: -media-jam-warning
D [11/Dec/2009:06:42:19 -0800] [Job 914] STATE: -input-tray-missing-warning
D [11/Dec/2009:06:42:19 -0800] [Job 914] STATE: -output-tray-missing-warning
D [11/Dec/2009:06:42:19 -0800] [Job 914] STATE: -marker-supply-missing-warning
D [11/Dec/2009:06:42:19 -0800] [Job 914] STATE: -output-area-almost-full-report
D [11/Dec/2009:06:42:19 -0800] [Job 914] STATE: -output-area-full-warning
D [11/Dec/2009:06:42:19 -0800] [Job 914] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=6, addr=0xb8f578c4, use_bc=1, side_cb=0xb78f9590)
D [11/Dec/2009:06:42:19 -0800] [Job 914] Print file sent, waiting for printer to finish...
D [11/Dec/2009:06:42:19 -0800] [Job 914] prtMarkerSuppliesLevel.1.1 = 0
D [11/Dec/2009:06:42:19 -0800] [Job 914] prtMarkerSuppliesLevel.1.2 = -3
D [11/Dec/2009:06:42:19 -0800] [Job 914] ATTR: marker-levels=0,0
D [11/Dec/2009:06:42:19 -0800] [Job 914] Ready to print.
D [11/Dec/2009:06:42:19 -0800] [Job 914] End of messages
D [11/Dec/2009:06:42:19 -0800] [Job 914] printer-state=3(idle)
D [11/Dec/2009:06:42:19 -0800] [Job 914] printer-state-message="Ready to print."
D [11/Dec/2009:06:42:19 -0800] [Job 914] printer-state-reasons=none

-----------------------Thunderbird Email----------------
D [11/Dec/2009:06:39:14 -0800] [Job 912] printer-state-message="Ready to print."                                              
D [11/Dec/2009:06:39:14 -0800] [Job 912] printer-state-reasons=none                                                           
E [11/Dec/2009:06:39:58 -0800] [Job 913] May not be a PDF file (continuing anyway)                                            
E [11/Dec/2009:06:39:58 -0800] [Job 913] PDF file is damaged - attempting to reconstruct xref table...                        
E [11/Dec/2009:06:39:58 -0800] [Job 913] Couldn't find trailer dictionary                                                     
E [11/Dec/2009:06:39:58 -0800] [Job 913] Couldn't read xref table                                                             
E [11/Dec/2009:06:40:03 -0800] [Job 913] Job stopped due to filter errors; please consult the error_log file for details.     
D [11/Dec/2009:06:40:03 -0800] [Job 913] The following messages were recorded from 06:39:58 to 06:40:03                       
D [11/Dec/2009:06:40:03 -0800] [Job 913] Adding start banner page "none".                                                     
D [11/Dec/2009:06:40:03 -0800] [Job 913] Queued on "E332n" by "rbroman".                                                      
D [11/Dec/2009:06:40:03 -0800] [Job 913] Auto-typing file...                                                                  
D [11/Dec/2009:06:40:03 -0800] [Job 913] Request file type is application/postscript.                                         
D [11/Dec/2009:06:40:03 -0800] [Job 913] File of type application/postscript queued by "rbroman".                             
D [11/Dec/2009:06:40:03 -0800] [Job 913] Adding end banner page "none".                                                       
D [11/Dec/2009:06:40:03 -0800] [Job 913] job-sheets=none,none                                                                 
D [11/Dec/2009:06:40:03 -0800] [Job 913] argv[0]="E332n"                                                                      
D [11/Dec/2009:06:40:03 -0800] [Job 913] argv[1]="913"                                                                        
D [11/Dec/2009:06:40:03 -0800] [Job 913] argv[2]="rbroman"                                                                    
D [11/Dec/2009:06:40:03 -0800] [Job 913] argv[3]="Re: Exploring Grant Ideas re Computers"                                     
D [11/Dec/2009:06:40:03 -0800] [Job 913] argv[4]="1"                                                                          
D [11/Dec/2009:06:40:03 -0800] [Job 913] argv[5]="finishings=3 media=na_letter_8.5x11in number-up=1 Resolution= job-uuid=urn:uuid:fd02a694-9b23-36b2-4ca0-67fab927bc81 job-originating-host-name=localhost"                                                 
D [11/Dec/2009:06:40:03 -0800] [Job 913] argv[6]="/var/spool/cups/d00913-001"                                                 
D [11/Dec/2009:06:40:03 -0800] [Job 913] envp[0]="CUPS_CACHEDIR=/var/cache/cups"                                              
D [11/Dec/2009:06:40:03 -0800] [Job 913] envp[1]="CUPS_DATADIR=/usr/share/cups"                                               
D [11/Dec/2009:06:40:03 -0800] [Job 913] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"                                      
D [11/Dec/2009:06:40:03 -0800] [Job 913] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"                                        
D [11/Dec/2009:06:40:03 -0800] [Job 913] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"                                           
D [11/Dec/2009:06:40:03 -0800] [Job 913] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"                                               
D [11/Dec/2009:06:40:03 -0800] [Job 913] envp[6]="CUPS_SERVERROOT=/etc/cups"                                                  
D [11/Dec/2009:06:40:03 -0800] [Job 913] envp[7]="CUPS_STATEDIR=/var/run/cups"                                                
D [11/Dec/2009:06:40:03 -0800] [Job 913] envp[8]="HOME=/var/spool/cups/tmp"                                                   
D [11/Dec/2009:06:40:03 -0800] [Job 913] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"                 
D [11/Dec/2009:06:40:03 -0800] [Job 913] envp[10]="SERVER_ADMIN=root@jboat17"                                                 
D [11/Dec/2009:06:40:03 -0800] [Job 913] envp[11]="SOFTWARE=CUPS/1.4.1"                                                       
D [11/Dec/2009:06:40:03 -0800] [Job 913] envp[12]="TMPDIR=/var/spool/cups/tmp"                                                
D [11/Dec/2009:06:40:03 -0800] [Job 913] envp[13]="TZ=America/Los_Angeles"                                                    
D [11/Dec/2009:06:40:03 -0800] [Job 913] envp[14]="USER=root"                                                                 
D [11/Dec/2009:06:40:03 -0800] [Job 913] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"                                       
D [11/Dec/2009:06:40:03 -0800] [Job 913] envp[16]="CUPS_ENCRYPTION=IfRequested"                                               
D [11/Dec/2009:06:40:03 -0800] [Job 913] envp[17]="IPP_PORT=631"                                                              
D [11/Dec/2009:06:40:03 -0800] [Job 913] envp[18]="CHARSET=utf-8"                                                             
D [11/Dec/2009:06:40:03 -0800] [Job 913] envp[19]="LANG=en_US.UTF-8"                                                          
D [11/Dec/2009:06:40:03 -0800] [Job 913] envp[20]="PPD=/etc/cups/ppd/E332n.ppd"                                               
D [11/Dec/2009:06:40:03 -0800] [Job 913] envp[21]="RIP_MAX_CACHE=803910k"                                                     
D [11/Dec/2009:06:40:03 -0800] [Job 913] envp[22]="CONTENT_TYPE=application/postscript"                                       
D [11/Dec/2009:06:40:03 -0800] [Job 913] envp[23]="DEVICE_URI=socket://192.168.0.4:9100"                                      
D [11/Dec/2009:06:40:03 -0800] [Job 913] envp[24]="PRINTER_INFO=E332n"                                                        
D [11/Dec/2009:06:40:03 -0800] [Job 913] envp[25]="PRINTER_LOCATION=jboat17"                                                  
D [11/Dec/2009:06:40:03 -0800] [Job 913] envp[26]="PRINTER=E332n"                                                             
D [11/Dec/2009:06:40:03 -0800] [Job 913] envp[27]="CUPS_FILETYPE=document"                                                    
D [11/Dec/2009:06:40:03 -0800] [Job 913] envp[28]="FINAL_CONTENT_TYPE=application/vnd.cups-postscript"                        
D [11/Dec/2009:06:40:03 -0800] [Job 913] Started filter /usr/lib/cups/filter/pstopdf (PID 5403)                               
D [11/Dec/2009:06:40:03 -0800] [Job 913] Started filter /usr/lib/cups/filter/pdftopdf (PID 5404)                              
D [11/Dec/2009:06:40:03 -0800] [Job 913] Started filter /usr/lib/cups/filter/cpdftocps (PID 5405)                             
D [11/Dec/2009:06:40:03 -0800] [Job 913] Started backend /usr/lib/cups/backend/socket (PID 5406)                              
D [11/Dec/2009:06:40:03 -0800] [Job 913] pstopdf 6 args: 913 rbroman Re: Exploring Grant Ideas re Computers 1 finishings=3 media=na_letter_8.5x11in number-up=1 Resolution= job-uuid=urn:uuid:fd02a694-9b23-36b2-4ca0-67fab927bc81 job-originating-host-name=localhost /var/spool/cups/d00913-001                                                                                         
D [11/Dec/2009:06:40:03 -0800] [Job 913] PPD: /etc/cups/ppd/E332n.ppd                                                         
D [11/Dec/2009:06:40:03 -0800] [Job 913] STATE: +connecting-to-device                                                         
D [11/Dec/2009:06:40:03 -0800] [Job 913] Looking up "192.168.0.4"...                                                          
D [11/Dec/2009:06:40:03 -0800] [Job 913] Connecting to 192.168.0.4:9100                                                       
D [11/Dec/2009:06:40:03 -0800] [Job 913] Connecting to printer...                                                             
D [11/Dec/2009:06:40:03 -0800] [Job 913] STATE: -connecting-to-device                                                         
D [11/Dec/2009:06:40:03 -0800] [Job 913] Connected to printer...                                                              
D [11/Dec/2009:06:40:03 -0800] [Job 913] Connected to 192.168.0.4:9100 (IPv4)...                                              
D [11/Dec/2009:06:40:03 -0800] [Job 913] pdftops argv[5] = 913 rbroman Re: Exploring Grant Ideas re Computers 1 finishings=3 media=na_letter_8.5x11in number-up=1 Resolution= job-uuid=urn:uuid:fd02a694-9b23-36b2-4ca0-67fab927bc81 job-originating-host-name=localhost
D [11/Dec/2009:06:40:03 -0800] [Job 913] PPD: /etc/cups/ppd/E332n.ppd
D [11/Dec/2009:06:40:03 -0800] [Job 913] /usr/bin/pdftops supports '-origpagesizes': yes
D [11/Dec/2009:06:40:03 -0800] [Job 913] PostScript Level: 2
D [11/Dec/2009:06:40:03 -0800] [Job 913] Duplex: no
D [11/Dec/2009:06:40:03 -0800] [Job 913] Resolution:
D [11/Dec/2009:06:40:03 -0800] [Job 913] eval: 1: job-uuid=urn:uuid:fd02a694-9b23-36b2-4ca0-67fab927bc81: not found
D [11/Dec/2009:06:40:03 -0800] [Job 913] hrDeviceDesc="Lexmark E332n 380GL63 141.C09 -- Part Number --"
D [11/Dec/2009:06:40:03 -0800] [Job 913] Resolution:
D [11/Dec/2009:06:40:03 -0800] [Job 913] prtMarkerColorantValue.1.1 = "black"
D [11/Dec/2009:06:40:03 -0800] [Job 913] eval: 1: job-uuid=urn:uuid:fd02a694-9b23-36b2-4ca0-67fab927bc81: not found
D [11/Dec/2009:06:40:03 -0800] [Job 913] ATTR: marker-colors=#000000,none
D [11/Dec/2009:06:40:03 -0800] [Job 913] ATTR: marker-names="Black Toner","Photo Drum"
D [11/Dec/2009:06:40:03 -0800] [Job 913] ATTR: marker-types=toner,opc
D [11/Dec/2009:06:40:03 -0800] [Job 913] ATTR: marker-levels=40,0
D [11/Dec/2009:06:40:03 -0800] [Job 913] STATE: -media-low-report
D [11/Dec/2009:06:40:03 -0800] [Job 913] STATE: -media-empty-warning
D [11/Dec/2009:06:40:03 -0800] [Job 913] STATE: -toner-low-report
D [11/Dec/2009:06:40:03 -0800] [Job 913] STATE: -toner-empty-warning
D [11/Dec/2009:06:40:03 -0800] [Job 913] STATE: -door-open-report
D [11/Dec/2009:06:40:03 -0800] [Job 913] STATE: -media-jam-warning
D [11/Dec/2009:06:40:03 -0800] [Job 913] STATE: -input-tray-missing-warning
D [11/Dec/2009:06:40:03 -0800] [Job 913] STATE: -output-tray-missing-warning
D [11/Dec/2009:06:40:03 -0800] [Job 913] STATE: -marker-supply-missing-warning
D [11/Dec/2009:06:40:03 -0800] [Job 913] STATE: -output-area-almost-full-report
D [11/Dec/2009:06:40:03 -0800] [Job 913] STATE: -output-area-full-warning
D [11/Dec/2009:06:40:03 -0800] [Job 913] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=6, addr=0xb90da8c4, use_bc=1, side_cb=0xb783f590)
D [11/Dec/2009:06:40:03 -0800] [Job 913] Print file sent, waiting for printer to finish...
D [11/Dec/2009:06:40:03 -0800] [Job 913] prtMarkerSuppliesLevel.1.1 = 0
D [11/Dec/2009:06:40:03 -0800] [Job 913] prtMarkerSuppliesLevel.1.2 = -3
D [11/Dec/2009:06:40:03 -0800] [Job 913] ATTR: marker-levels=0,0
D [11/Dec/2009:06:40:03 -0800] [Job 913] Ready to print.
D [11/Dec/2009:06:40:03 -0800] [Job 913] End of messages
D [11/Dec/2009:06:40:03 -0800] [Job 913] printer-state=3(idle)
D [11/Dec/2009:06:40:03 -0800] [Job 913] printer-state-message="Ready to print."
D [11/Dec/2009:06:40:03 -0800] [Job 913] printer-state-reasons=none

---

