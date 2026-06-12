---
title: "complier errors on program install"
date: 2010-03-23
forum: General Help
---

### Post by melissaif on 2010-03-23
I am new to Ubuntu and have been attempting to install a program called GATE (opengatecollaboration.org) for a week now. I am ALMOST there, but am receiving the following compiler errors: 

FIRST ERROR MESSAGES
src/GateEventAction.cc:120: error: â€˜GateToRootâ€™ was not declared
in this scope
src/GateEventAction.cc:120: error: â€˜gateToRootâ€™ was not declared
in this scope

src/GateAnalysis.cc:316: error: â€˜GateToRootâ€™ was not declared in this scope
src/GateAnalysis.cc:316: error: â€˜gateToRootâ€™ was not declared in this scope
src/GateAnalysis.cc:316: error: expected primary-expression before â€˜)â€™ token
src/GateAnalysis.cc:317: error: â€˜ComptonRayleighDataâ€™ was not
declared in this scope
src/GateAnalysis.cc:317: error: expected â€˜;â€™ before â€˜aCRDataâ€™
src/GateAnalysis.cc:318: error: â€˜aCRDataâ€™ was not declared in this scope
src/GateAnalysis.cc:333: error: â€˜GateToRootâ€™ was not declared in this scope
src/GateAnalysis.cc:333: error: â€˜gateToRootâ€™ was not declared in this scope
src/GateAnalysis.cc:333: error: expected primary-expression before â€˜)â€™ token
src/GateAnalysis.cc:334: error: â€˜ComptonRayleighDataâ€™ was not
declared in this scope
src/GateAnalysis.cc:334: error: expected â€˜;â€™ before â€˜aCRDataâ€™
src/GateAnalysis.cc:335: error: â€˜aCRDataâ€™ was not declared in this scope


I can go into the source and see the following pertaining to the first two errors, but I am not great with C so I am not sure what to do with this. Any ideas?

%%%%%%%%%%%%%%%%%
EXCERPT FROM GateEventAction.cc:
%%%%%%%%%%%%%%%%%

//   RECORD THE PHANTOM HITS COLLECTION OF THE CURRENT EVENT                                                                        
                 GateToRoot* gateToRoot = (GateToRoot*) (GateOutputMgr::GetInstance()->GetModule("root"));
// STORE TO A ROOT FILE  THE DATA COLLECTED IN THE RECORDSTEP METHOD DURING STEPPING                                                
                 gateToRoot->RecordRecStepData( evt );

%%%%%%%%%%%%%%%
EXCERPT FROM Gate2Root.hh:
%%%%%%%%%%%%%%%

class GateToRoot :  public GateVOutputModule
{
public:

File Edit Options Buffers Tools C++ Help                                                                                            

  GateToRoot(const G4String& name, GateOutputMgr* outputMgr,DigiMode digiMode);
  virtual ~GateToRoot();

120: GateToRoot(const G4String& name, GateOutputMgr* outputMgr,DigiMode digiMode);

---

### Post by melissaif on 2010-03-23
I see that this thread has been viewed several times but not replied to--please let me know what I can do to phrase my question in a way to facilitate receiving answers.

Thanks!

---

