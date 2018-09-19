# NanoHRT-tools

### Set up CMSSW

```bash
cmsrel CMSSW_9_4_10
cd CMSSW_9_4_10/src
cmsenv
```

### Set up official NanoAOD-tools

```bash
git clone https://github.com/cms-nanoAOD/nanoAOD-tools.git PhysicsTools/NanoAODTools
```

### Get customized NanoAOD tools for HeavyResTagging (NanoHRT-tools)

```bash
git clone https://github.com/hqucms/NanoHRT-tools.git PhysicsTools/NanoHRTTools
```

### Compile

```bash
scram b -j8
```

### Test

Instructions to run the nanoAOD postprocessor can be found at [nanoAOD-tools](https://github.com/cms-nanoAOD/nanoAOD-tools#nanoaod-tools). 

### Production

 - To make trees for MC performance study (currently supports only condor at FNALLPC):

```bash
cd PhysicsTools/NanoHRTTools/run
python runPostProcessing.py /path/of/input /path/to/output --friend -I PhysicsTools.NanoHRTTools.producers.hrtMCTreeProducer hrtMCTree
```

 - To resubmit failed jobs, run the same command but add `--resubmit`.

More options of `runPostProcessing.py` can be found with `python runPostProcessing.py -h`.