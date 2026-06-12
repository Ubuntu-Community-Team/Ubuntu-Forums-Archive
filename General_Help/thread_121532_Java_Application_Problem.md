---
title: "Java Application Problem"
date: 2006-01-25
forum: General Help
---

### Post by russbuss on 2006-01-25
I have a java application, written by someone other than me, that I am using to anlayze a slew of data.  The application requires Sun jdk 1.5 to run and I have seemingly successfully installed jdk 1.5; I am able to launch the application without incident.

However, when I attempt to begin analyzing data with this application, I get a bunch of java errors spit out which I have pasted below.  My question is whether these errors are indicative of an incompatibility wrought by using jdk 1.5 on Ubuntu or indicative of an incompatibility wrought by the application.  I realize that this isn't a great distinction, but my point is as follows:

I'm wondering whether these errors can be solved by re-coding part(s) of the application to work with java on Ubuntu, or whether I need to wait for future tweaks to java on Ubuntu.  If it's the former I, or my programming friends can (hopefully) solve the problem; if it's the latter, I'm screwed.

Thanks for any help.


-Ben.



Error Log:

Exception in thread "Thread-1" java.lang.NullPointerException
	at edu.ucsc.neurobiology.vision.plot.PlotPanel.resiveHappened(PlotPanel.java:519)
	at edu.ucsc.neurobiology.vision.plot.PlotPanel.stateChanged(PlotPanel.java:529)
	at edu.ucsc.neurobiology.vision.plot.Axis.setScreenRange(Axis.java:96)
	at edu.ucsc.neurobiology.vision.plot.AxesBorder.getBorderInsets(AxesBorder.java:119)
	at javax.swing.JComponent.setBorder(JComponent.java:1749)
	at edu.ucsc.neurobiology.vision.plot.PlotPanel.<init>(PlotPanel.java:105)
	at edu.ucsc.neurobiology.vision.plot.PlotPanel.<init>(PlotPanel.java:82)
	at edu.ucsc.neurobiology.vision.view2d.NeuronViewer.makeMosaicPanel(NeuronViewer.java:1319)
	at edu.ucsc.neurobiology.vision.view2d.NeuronViewer.valueChanged(NeuronViewer.java:1007)
	at javax.swing.JTree.fireValueChanged(JTree.java:2399)
	at javax.swing.JTree$TreeSelectionRedirector.valueChanged(JTree.java:2770)
	at javax.swing.tree.DefaultTreeSelectionModel.fireValueChanged(DefaultTreeSelectionModel.java:629)
	at javax.swing.tree.DefaultTreeSelectionModel.notifyPathChange(DefaultTreeSelectionModel.java:1078)
	at javax.swing.tree.DefaultTreeSelectionModel.setSelectionPaths(DefaultTreeSelectionModel.java:287)
	at javax.swing.JTree.setSelectionPaths(JTree.java:1187)
	at javax.swing.JTree.setSelectionRows(JTree.java:1260)
	at javax.swing.JTree.setSelectionRow(JTree.java:1235)
	at edu.ucsc.neurobiology.vision.view2d.NeuronViewer.<init>(NeuronViewer.java:251)
	at edu.ucsc.neurobiology.vision.gui.DataManager$4.run(DataManager.java:178)

---

