---
title: "SNMP and CPU stats"
date: 2010-12-05
forum: General Help
---

### Post by paped on 2010-12-05
I have an issue with my MRTG/SNMP CPU stats currently, on 10.04 all my stats were working, after upgrading to 10.10 none of them worked until I added the ACPI "Lax" command to the Grub config at that point all stats except the CPU one started to work. To be honest I could not see why the CPU stats were not working so I gave up, however last week I did a couple of "Apt-get upgrades" after the first one the graph seemed to come to life but showed very low incorrect data, after the 2nd one late last week the CPU stats started working correctly without me doing anything. However I had to reboot my machine last night and they have stopped again, but other than the reboot I have done nothing else to stop them. Again is only the CPU stats that are broken my fan speed, voltages, memory usage that I also monitor all work fine.

Can anybody advise what this may be, if you have had similar problems do you know the fix for it....?

I have put the relevant bit from my MRTG.cfg file below for info this is the same as it has been for 3 versions of Ubuntu now but something in 10.10 does not seem to like the CPU bit.

#
# CPU
#
Target[server.cpu0]:ssCpuRawUser.0&ssCpuRawUser.0:public@127.0.0.1+ssCpuRawSystem.0&ssCpuRawSystem.0:public@127.0.0.1+ssCpuRawNice.0&ssCpuRawNice.0:public@127.0.0.1
MaxBytes[server.cpu0]: 100
Title[server.cpu0]: Server CPU Load
PageTop[server.cpu0]: <H1>Active CPU Load % -- server</H1>
		<div id="sysdetails">
			<table>
				<tr>
					<td>Description:</td>
					<td>CPU  </td>
				</tr>
			</table>
		</div>
Unscaled[server.cpu0]: ymwd
ShortLegend[server.cpu0]: %
YLegend[server.cpu0]: CPU Utilization %
Legend1[server.cpu0]: Active CPU in % (Load)
LegendI[server.cpu0]: Active CPU %
LegendO[server.cpu0]:
Legend2[server.cpu0]:
Legend3[server.cpu0]: Active CPU % (Maximal 5 Minute)
Legend4[server.cpu0]:
Options[server.cpu0]: growright,nopercent


Thanks in advance for any help and advice you can give....

---

