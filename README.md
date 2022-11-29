# Part Testing, With Purpose

The stock "part testing" contract suite in KSP 1 regularly comes up with contracts that are inane even for Kerbal standards (_Test LY-01 Fixed Landing Gear on a suborbital trajectory around Jool_), extremely grindy (Haul $RANDOM_PART to the launch pad. Press 'test part' in the part menu. Rinse. Repeat.) or both. This contract pack mod tries to fix that.

In addition, this contract pack tries to provide interesting game play together with part reliability/part failure mods, especially part failure mods based on [TestFlight](https://forum.kerbalspaceprogram.com/index.php?/topic/99043-122-testflight-v180-01-may-2017-bring-flight-testing-to-ksp/). First class support for [Less Real Test Flight](https://forum.kerbalspaceprogram.com/index.php?/topic/205848-wipv093-less-real-test-flight-testflight-for-stock-and-stockalike-parts-ksp-112x/) is built in from the start, and has a big influence on the overall design of the contract pack.

## Gameplay Overview

### Contract Types

Contracts provided by this mod still follow the general schema of _"Test $SOME_PART in $SOME_SCENARIO"_, and the bulk of the contracts is still generated proceurally. But each scenario tells a plausible story, and the parts are chosen to fit the scenario. For example:

* _Test a new first stage based on the RE-M3 "Mainsail" Liquid Fuel Engine in flight_: The contract requires launching a new vessel that has a "Mainsail" engine and a tank that can feed the engine. To complete the contract, the "Mainsail" engine has to be started while still on the launch pad and must be active while the vessel is flying in atmosphere.
* _Test a new probe based on the Probodobodyne QBE probe core_ in orbit: The contract requires to launch a vessel that has a "QBE" probe core, and may optionally have RCS, reaction wheel, and antenna parts (including the optional parts gives a bonus reward). Contract completes when the vessel reaches a stable orbit.
* _Test a modified probe based on the Probodobodyne QBE probe core in orbit_: The contract unlocks when the contract above has been completed. It requires a vessel with almost the same probe core, but at least one of the optional parts has to be different. Contract completes when the vessel reaches a stable orbit.

Some contracts may provide special scenarios to support testing special parts, for example:
* _Test the atmospheric launch abort procedure for the Mk1-3 Command Pod_: The contract requires a vessel with the Mk1-3 command pod and the Launch Escape System. To complete the contract, the LES must be activated in flight in the atmosphere, and the command pod must be recovered.

### Contract Rewards

Part testing contract rewards are moderate (this is part testing, after all, not exciting new science):
* Basic funds rewards are just a bit more than the cost of the tested part. Part costs are payed out in advance, anything over the pure part costs is payed on successful completion.
* Basic science rewards are on the order of one science point per tested part.
* Standard reputation reward is zero
* Standard contract prestige is "Trivial"

Most contracts will give an extra bonus when the tested parts are recovered. That bonus reward is typically an increase of the science rewards by a small factor (greater than one, probably less than two), and one reputation point.

Occasionally, contracts which have a bonus goal are offered with prestige level "Significant". These contracts _require_ the bonus goal (usually part recovery) to be met for completion, and increase all rewards (including funds) so that they are a bit more than the corresponding contract at prestige "Trivial" including the bonus reward.

No part testing contracts with prestige level "Exceptional" are offered. This _is_ part testing, after all.

#### Modified Reward System With TestFlight

When TestFlight is installed, the _real_ reward for taking part test contracts shifts to its natural target: Making parts more reliable.

With TestFlight, parts accumulate "data units" while they are in active use (e.g. an engine is fired, a parachute is deployed, a tank is drained, ...). The amount of data units present on a part at launch determines how reliable that part is.

So, with TestFlight installed, test contracts will pay out additional data units instead of science points (which are a poor substitute, really): 
* Completing a test contract multiplies the data units acquired during the test for each tested part by a given factor > 1
* That factor increases when the bonus goal is met
* The factor increases again when the contract has "Significant" prestige

### Penalties for failure

Typically, part test contracts do not fail when the contract parameters are not met, meaning they can be repeated until success. Test contracts may expire (or can be declined) without any penalty besides having to repay the advance funds.

The exception to this is killing crew members while testing. After all, an important purpose of testing parts is to _avoid_ killing crew. Therefore, killing crew members while testing immediately fails the contract, and _does_ carry a substantial penalty (mainly in reputation). 

### Part selection

Part selection generally considers only parts that have already been researched. Ocasionally, experimental parts from a node that is about to be researched may be offered, but this is rare.

Part selection generally favors testing "new" parts:
* Parts that have been researched but not yet unlocked
* Parts that have not been tested before
* Parts that are not on any vessel
* ...

#### Modified Part Selection With TestFlight

With TestFlight installed, part selection is biased a bit differently:
* Unreliable parts _in active use on a mission that is not covered by an active part testing contract_ are much more likely to be selected for testing than any other part (you _really_ should have tested those parts before flying them on a mission, after all).
* Next up are unreliable parts that have been tested before (if you did test it, it stands to reason that you want to use it. And if you want to use it, it should be reliable).
* And last, there are all those untested new parts out there (to get you started on building your next generation _reliable_ space craft)

# Installation

At the moment, only a development version is available. The recommended way to install is to directly clone the GitHub repository in your GameData directory:

~~~
cd $KSP_DIR/GameData
git clone https://github.com/rkunze/PartTestingWithPurpose.git
~~~

This requires that you have Git installed on your computer, but allows to update Embedded kOS Kirkuits later on with a simple git pull.

As an alternative if you do not have a Git client, [download the current development status](https://github.com/rkunze/PartTestingWithPurpose/archive/refs/heads/main.zip), unpack the zip file within your `GameData` directory, and rename `GameData/PartTestingWithPurpose-main` to `GameData/PartTestingWithPurpose`. For updates, you need to delete the `GameData/PartTestingWithPurpose` directory and reinstall from scratch in this case.
