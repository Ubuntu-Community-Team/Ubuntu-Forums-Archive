---
title: "xml mapping to fields"
date: 2012-06-08
forum: General Help
---

### Post by ELMIT on 2012-06-08
I need some help to get clear what I am looking for in Google ;-)

I got an XML respond and I need to put this into a database.

> <response>
	<version>2.9</version>
	<timestamp>2012-06-08 06:55:15</timestamp>
	<task_count>1</task_count>
	<task>
		<action>171718</action>
		<vertragid>00000011111</vertragid>
		<status>
			<code>200</code>
			<message>Erfolgreich.</message>
		</status>
		<data>
			<id>yo2</id>
			<name>Cramp GmbH &amp; Co. OHG</name>
			<url>http://www.cramp.de</url>
		</data>
		<customerid>14118907</customerid>
	</task>
	<sessionid>20120608065515-api2-63245</sessionid>
</response>

from that I want to get fields like $customerid = 14118907 ....

How to do, or how to ask in Google to find the solution?

---

### Post by ELMIT on 2012-06-08
Found it with SimpleXML, ...

---

