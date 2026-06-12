---
title: "Studio Tax (free software for windows) + wine"
date: 2010-03-21
forum: General Help
---

### Post by prdolino on 2010-03-21
Hello,

I have been trying to get Studio Tax to run in wine 1.1.41. To do so I installed .NET Framework 2.0 (required by Studio Tax) using [[COLOR="Blue"]_THIS_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=943298"). I then installed [[COLOR="blue"]_Studio Tax_[/COLOR]]("http://www.studiotax.com/ver09/StudioTaxInstall09.exe"). I ran the .exe file using wine and the installation worked like a charm.

When I try to run the installed program I get the following error:

> 
Error Message: 
Not implemented.

Error Source: 
System.Drawing

Details: 
   at System.Drawing.Font.GetHeight(Graphics graphics)
   at System.Drawing.Font.get_SizeInPoints()
   at System.Windows.Forms.Internal.WindowsFont.FromFont(Font font, WindowsFontQuality fontQuality)
   at System.Windows.Forms.Internal.WindowsGraphicsCacheManager.GetWindowsFont(Font font, WindowsFontQuality fontQuality)
   at System.Windows.Forms.TextRenderer.MeasureText(String text, Font font)
   at System.Windows.Forms.ToolStripItem.GetTextSize()
   at System.Windows.Forms.ToolStripDropDownMenu.CalculateInternalLayoutMetrics()
   at System.Windows.Forms.ToolStripDropDownMenu.OnLayout(LayoutEventArgs e)
   at System.Windows.Forms.Control.PerformLayout(LayoutEventArgs args)
   at System.Windows.Forms.Control.PerformLayout()
   at System.Windows.Forms.Control.ResumeLayout(Boolean performLayout)
   at System.Windows.Forms.Layout.LayoutTransaction.Dispose()
   at System.Windows.Forms.ToolStripDropDown.OnOwnerItemFontChanged(EventArgs e)
   at System.Windows.Forms.ToolStripMenuItem.OnFontChanged(EventArgs e)
   at System.Windows.Forms.ToolStripItem.SetOwner(ToolStrip newOwner)
   at System.Windows.Forms.ToolStripItemCollection.SetOwner(ToolStripItem item)
   at System.Windows.Forms.ToolStripItemCollection.Add(ToolStripItem value)
   at System.Windows.Forms.ToolStripItemCollection.AddRange(ToolStripItem[] toolStripItems)
   at StudioTax.StudioTaxApp.CreateMenu()
   at StudioTax.StudioTaxApp..ctor(String[] args)
   at StudioTax.StudioTaxApp.BQ46u3JfM(String[] )


At first this error is very difficult to read due to the fudged up fonts. To fix the fonts I did [[COLOR="blue"]_THIS_[/COLOR]]("http://bbs.archlinux.org/viewtopic.php?id=62334").

I have done further research on the subject and found no other option than to ask here   :)    Hope someone can share a piece of their mind.

Thanks!

---

### Post by asmoore82 on 2010-03-21
licensing, not price, it whats makes free software free: [http://www.gnu.org/philosophy/free-sw.html](http://www.gnu.org/philosophy/free-sw.html)

I would suggest VirtualBox instead of Wine for software that requires .Net.

---

### Post by prdolino on 2010-03-22
Free, you got me there with a technicality  :P

As for VirtualBox... wow, that app is the bomb and I never heard of it until now. Thank you so much!!   :D

---

