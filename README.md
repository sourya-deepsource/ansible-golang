# ansible-golang

Installs the golang tools on a Ubuntu/Debian machine.

## Requirements

### CPU architecture:

* x86_64 / amd64
* armv7l / armhf
* aarch64 / arm64

### Operating systems:

* Ubuntu:
  * 16.04 (xenial)
  * 18.04 (bionic)
  * 20.04 (focal)
* Debian
  * 9 (stretch)
  * 10 (buster)

## Role parameters

| Variable       | Type | Mandatory? | Default | Description           |
|----------------|------|------------|---------|-----------------------|
| golang_version | text | no         | `1.14.4` | The golang version   |

## Usage

### Add to `requirements.yml`

```yaml
- name: install-golang
  src: https://github.com/borisskert/ansible-golang.git
  scm: git
```

### example `playbook.yml`

```yaml
- hosts: test_machine
  become: yes

  roles:
    - role: install-golang
      golang_version: 1.14.4
```

## Testing

Requirements:

* [Ansible](https://docs.ansible.com/)
* [Molecule](https://molecule.readthedocs.io/en/latest/index.html)
* [yamllint](https://yamllint.readthedocs.io/en/stable/#)
* [ansible-lint](https://docs.ansible.com/ansible-lint/)
* [Docker](https://docs.docker.com/)

### Run within docker

```shell script
molecule test \
&& molecule test -s fixed-latest-version \
&& molecule test -s fixed-older-version \
&& molecule test -s upgrade-version
```

I recommend to use [pyenv](https://github.com/pyenv/pyenv) for local testing.
Within the Github Actions pipeline I use [my molecule Docker image](https://github.com/borisskert/docker-molecule).

## License

MIT

## Author Information

* [borisskert](https://github.com/borisskert)
