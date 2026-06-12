---
title: "xdmcp with lightdm (to cygwin)"
date: 2012-01-26
forum: General Help
---

### Post by treii28 on 2012-01-26
I used to use an xdmcp login on my old ubuntu and just installed ubuntu 11.10 on one of my laptops to learn it doesn't use gdm anymore, but uses lightdm. I can't seem to get xdmcp to connect now and the resources to set it up appear to be less than abundant.

I found some links that suggested adding the following to /etc/lightdm/lightdm.conf:

[XDMCPServer]
enabled=true

[SeatDefaults]
xserver-allow-tcp=true

Now I am at least getting responses in the lightdm logs, but it's still not connecting. Cygwin command is:

c:\cygwin\bin\run -p /usr/bin  XWin :1.0 -query %REMOTE_HOST% -nodecoration -lesspointer -fp tcp/%REMOTE_HOST%:7100

Where REMOTE_HOST is the address of my lightdm machine.
It goes to black but then dies with error (1)

lightdm.log shows:
DEBUG: Starting XDMCP server on UDP/IP port 177
 in the starup details

cygwin request shows up as:
[+78832.33s] DEBUG: Got Request(display_number=1 connections=[(0, C0A80144) (0, C0A80223) (6, FE80000000000000B0C56E092289C2DE) (6, FE8000000000000020952F1EC60D885B) (6, FE8000000000000000005EFEC0A80144) (6, FE8000000000000000005EFEC0A80223) (6, 2001000041379E76088B3A669D055B2A) (6, FE80000000000000088B3A669D055B2A)] authentication_name='' authentication_data= authorization_names=['MIT-MAGIC-COOKIE-1' 'XDM-AUTHORIZATION-1'] manufacturer_display_id='')
[+78832.33s] DEBUG: Send Accept(session_id=20111 authentication_name='' authentication_data= authorization_name='MIT-MAGIC-COOKIE-1' authorization_data=F11775E77411A11309EF2CFD3B633F80)
[+78832.33s] DEBUG: Got Manage(session_id=20111 display_number=1 display_class='MIT-unspecified')
[+78832.33s] DEBUG: Starting seat
[+78832.33s] DEBUG: Starting new display for greeter
[+78832.33s] DEBUG: Connecting to XServer 2001:0:4137:9e76:88b:3a66:9d05:5b2a:1
[+78832.33s] DEBUG: Error connecting to XServer 2001:0:4137:9e76:88b:3a66:9d05:5b2a:1
[+78832.33s] DEBUG: Send Failed(session_id=20111 status='Failed to connect to display :1')
[+78832.34s] DEBUG: Timing out unmanaged session 20111

I verified XWin is in the windows firewall rules with an enabled exemption. What am I missing to make this work?

SW

---

