# RoboWeldAR ROSE-AP

[![Documentation Status](https://readthedocs.org/projects/roboweldar-rose-ap/badge/?version=latest)](https://roboweldar-rose-ap.readthedocs.io/en/latest/?badge=latest)
[![CII Best Practices](https://bestpractices.coreinfrastructure.org/projects/4822/badge)](https://bestpractices.coreinfrastructure.org/projects/4822)
[![Codacy Badge](https://app.codacy.com/project/badge/Grade/97c7794bcfc4435e807d3f6838088cfc)](https://www.codacy.com/gh/ikh-innovation/roboweldar-rose-ap/dashboard?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=ikh-innovation/roboweldar-rose-ap&amp;utm_campaign=Badge_Grade)

Coordinator docker build status:
![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/roboweldar/roboweldar-coordinator?style=plastic)
[Coordinator Docker](https://hub.docker.com/r/roboweldar/roboweldar-coordinator)

3D reconstruction docker build status:
![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/roboweldar/roboweldar-3d-reconstruction?style=plastic)
[3D reconstruction Docker](https://hub.docker.com/r/roboweldar/roboweldar-3d-reconstruction)

Weld seam detection docker build status:
![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/roboweldar/roboweldar-weld-seam-detection?style=plastic)
[Weld seam detection Docker](https://hub.docker.com/r/roboweldar/roboweldar-weld-seam-detection)

![License: Apache 2.0](https://img.shields.io/github/license/ikh-innovation/roboweldar-rose-ap)

Not yet implemented:
[![CI](https://github.com/ramp-eu/TTE.project1/workflows/CI/badge.svg)](https://github.com/ramp-eu/TTE.project1/actions?query=workflow%3ACI)
[![Coverage Status](https://coveralls.io/repos/github/ramp-eu/TTE.project1/badge.svg?branch=master)](https://coveralls.io/github/ramp-eu/TTE.project1?branch=master)

This project is part of [DIH^2](http://www.dih-squared.eu/). For more information check the RAMP Catalogue entry for the
[components](https://github.com/xxx).

| :books: [Documentation](https://roboweldar-rose-ap.readthedocs.io/en/latest/) | :whale: [Docker Hub](https://hub.docker.com/u/roboweldar) |
| --------------------------------------------- | ------------------------------------------------------------- |


## Contents

- [Summary](#summary)
- [Background](#background)
- [Install](#install)
- [Cloning this repository](#cloning-this-repository)
- [Usage](#usage)
- [API](#api)
- [Architecture](#architecture)
- [Testing](#testing)
- [Contribution Guidelines](#contribution-guidelines)
- [License](#license)

## Summary

Given a set of photographs of a metallic object destined for welding, this module produces 3D-reconstructed model of that object, along with proposed welding paths.

## Background

This repository contains the source code to the RoboWeldAR ROSE-AP module. Given a set of photographs of a metallic object destined for welding, this module produces 3D-reconstructed model of that object, along with proposed welding paths. The ROSE-AP building block is one of the functional cores of the RoboWeldAR system (along with the robotic control module), and encapsulates the 3D reconstruction and weld seam detection components.

![High-level architecture](rose-ap-arch.png)

| Image dataset | 3D reconstructed model + proposed seams |
|---------------|-----------------------------------------|
|      <img src="assets/example_1_collage.png" width="500">    |       <img src="assets/example_1_reconstruction.gif" width="500">    |


- Inputs: An array of photos from different angles, camera pose for each photo 

- Outputs: 3D reconstructed object, welding trajectories (paths and poses) that represent where welding targets should be welded and how they should be approached. A simplified mesh file is also produced, for use in robotic path planning computations.

- Description: The most time-consuming part of the RoboWeldAR workflow is the 3-D reconstruction, which is why in our implementation we have developed a logger which broadcasts updates to the Orion Context Broker in NGSIv2 format, so that the user can monitor the progress. This ROSE-AP will be of interest to manufacturing entities that already use robotic welding processes in their workflow. The only modification to the hardware required is the addition of an off-the-shelf RGB camera, and a way to collect robot pose for each photograph capture so that it can be provided to the ROSE-AP component. After the output is produced and sent back to the end user, the end user must provide a way to provide the produced welding trajectory to their robot. As long as the robot frame has not been translated or rotated between the photo capture and welding processes, the welding trajectory will remain valid and ready for utilization.

## Cloning this repository

```bash
git clone --recursive git@github.com:ikh-innovation/roboweldar-rose-ap.git
```

Since the submodules in this repository were added using SSH, you will need to have SSH access enabled on your Github account to fully clone this repository.

## Install

Information about how to install the component can be found at the corresponding section of the
[Installation & Administration Guide](installationguide.md).

A `Dockerfile` is also available for your use - further information can be found [here](docker_guide.md)

## Usage

Information about how to use the component can be found in the [User & Programmers Manual](usermanual.md).

## API

Definition of the API interface:

Information about the API of  the component can be found in the [API documentation](api.md).

## Architecture

A description of the architecture can be found in the [Architecture section](architecture.md).

## Testing

For performing a basic end-to-end test, you have to follow the steps detailed in the [Test documentation](test_examples.md).

## Contribution Guidelines

For details on how to contribute, please refer to the [Contribution Guidelines](contribution.md).

## License

[Apache](LICENSE) © IKH 2021
