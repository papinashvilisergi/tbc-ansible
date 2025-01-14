# tbc-ansible
# Ansible Task #1

## ინსტრუქციები

დავალების მიზანია Ubuntu-ს ოპერაციული სისტემის კონფიგურაცია Ansible Playbook-ის და ინვენტორის გამოყენებით. დავალების დასრულების შემდეგ, ავტვირთე პროექტი GitHub-ზე და შექმენი PDF დოკუმენტაცია პროექტის მისამართით.

### მოთხოვნები

1. **ცვლადების გამოყენება Playbook-ში დინამიურობისთვის.**
2. **დროის სარტყელის შეცვლა**: `Asia/Tbilisi`.
3. **ჰოსთნეიმის შეცვლა**: `inventory_hostname`-ით.
4. **Firewall-ის გათიშვა.**
5. **SSHD-ის კონფიგურაცია დინამიურად**:
    - `port`
    - `LoginGraceTime`
    - `PermitRootLogin`
    - `MaxAuthTries`
    - `PasswordAuthentication`
6. **პაკეტების ინსტალაცია ერთ Task-ად**:
    - `vim`, `mc`, `wget`, `tree`, `bash-completion`, `ca-certificates`, `unzip`, `figlet`, `traceroute`, `tcpdump`, `nfs-common`
7. **Root მომხმარებლის პაროლის შეცვლა.**
8. **SSH ბანერის დამატება**:
    ```text
    Unauthorized Access is strictly prohibited. TBC Academy
    ```
9. **Superuser-ის შექმნა**:
    - მომხმარებლის სახელი: `superuser`
    - უფლებები: `sudoer`
    - დაამატეთ `SSH` public key.
10. **დამატებითი Task ფაილების შექმნა**:
    - `node_exporter` და `fluent-bit` ინსტალაციისთვის.

---

## ინსტალაციის ნაბიჯები

1. შევქმენი `inventory.yml` ფაილი.
2. დავწერე `site.yml` Playbook ფაილი.
3. გამოვიყენე `tasks` ფაილები საჭირო კონფიგურაციებისთვის.
4. ჩავრთე Playbook შემდეგი ბრძანებით:
    ```bash
    ansible-playbook -i inventory.yml site.yml --ask-become-pass
    ```

---

## შედეგების გადამოწმებისთვის გამოვიყენე შემდეგი კომანდები

- **დროის სარტყელი**:
    ```bash
    timedatectl | grep "Time zone"
    ```
- **ჰოსთნეიმი**:
    ```bash
    hostnamectl | grep "Static hostname"
    ```
- **Firewall-ის სტატუსი**:
    ```bash
    sudo ufw status
    ```
- **SSHD პარამეტრები**:
    ```bash
    grep -E "Port|LoginGraceTime|PermitRootLogin|MaxAuthTries|PasswordAuthentication" /etc/ssh/sshd_config
    ```
- **დაინსტალირებული პაკეტები**:
    ```bash
    dpkg -l | grep -E "vim|mc|wget|tree|bash-completion|ca-certificates|unzip|figlet|traceroute|tcpdump|nfs-common"
    ```
- **Node Exporter**:
    ```bash
    curl http://localhost:9100/metrics
    ```
- **Fluent Bit Docker კონტეინერი**:
    ```bash
    sudo docker ps | grep fluent-bit
    ```

---

## ატვირთვის ინსტრუქციები

1. ავტვირთე პროექტი GitHub პლატფორმაზე.
2. შექმენი PDF დოკუმენტაცია, რომელიც მოიცავს:
    - ინსტრუქციებს.
    - Playbook-ის კოდის ნაწილს.
    - შემოწმების შედეგებს.
    - Git რეპოს მისამართს.

---

**დამატებითი ინფორმაცია**  
თუ ანსიბლის ინსტრუქციებზე კითხვები გექნებათ გთხოვთ, დამიკავშირდეთ ან იხილოთ Ansible-ის ოფიციალური დოკუმენტაცია უკეთ გასაგებად კომანდების: [Ansible Documentation](https://docs.ansible.com/).
