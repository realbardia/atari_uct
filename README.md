# atari_uct
Upper Confidence Tree Planner for ATARI games

### Compile the codes:

-- First you need to install dependencies. on Ubuntu:

```bash
sudo apt-get install libopencv-dev libcaffe-cpu-dev libgflags-dev libgoogle-glog-dev libprotobuf-dev libboost-thread-dev libboost-system-dev libboost-dev libblas-dev cmake git
```

-- Next clone xitari and build it:

```bash
git clone https://github.com/deepmind/xitari.git
cd xitari
cmake -DCMAKE_BUILD_TYPE=release -DCMAKE_INSTALL_PREFIX=/usr .
make -j2
sudo make install
```

-- and build project at the end:

```bash
make
```



### run UCT on ATARI games

To run project just run below command:

```
./atariUCTPlanner -rom_path=${HOME}/subsystem/roms/ms_pacman.bin -depth=25 -num_traj=100 -save_data=true -save_path=output
```

-- depth and num_traj specify the planning depth and number of sampled trajectories

-- rom_path specify the game ROM

-- if save_data is true, then UCT planning data is saved in the folder specified by save_path. In the above example, the game frames are stored in output/frames folder, and actions are stored in output/act 

### Training using caffe-dev

-- a sample trajectory data is stored in output.tar.gz. train_sample shows how to train a neural network given the sample data

-- step 1: generate pixel-wise mean: ./preprocess.sh (assume caffe-dev binaries are in your PATH)

-- step 2: train the neural network: ./train.sh 
