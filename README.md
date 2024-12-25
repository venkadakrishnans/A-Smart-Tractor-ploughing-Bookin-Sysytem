<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BR Construction - Client Request</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" rel="stylesheet">
    <style>
        /* Resetting margins and paddings */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Roboto', sans-serif;
            background-color: #001f3f;
            line-height: 1.6;
        }

        /* Header Section */
        header {
            background-color: #ffbf00;
            padding: 20px 0;
            text-align: center;
            border-bottom: 2px solid #0056b3;
        }

        header .logo {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 10px;
        }

        header .logo img {
            height: 50px;
        }

        header .logo h1 {
            font-size: 2.2rem;
            color: white;
        }

        /* Main Container */
        .container {
            width: 90%;
            max-width: 800px;
            margin: 40px auto; /* Center the container */
            padding: 20px;
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        }

        h2 {
            color: #0056b3;
            margin-bottom: 20px;
            text-align: center;
            font-size: 2rem; /* Larger font for headings */
        }

        /* Form Section */
        .input-container {
            margin-bottom: 20px;
        }

        label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
            color: #333;
        }

        input, select, textarea {
            width: 100%;
            padding: 14px;
            font-size: 16px;
            border: 1px solid #ccc;
            border-radius: 5px;
            transition: border-color 0.3s ease;
        }

        input:focus, select:focus, textarea:focus {
            outline: none;
            border-color: #0056b3;
            box-shadow: 0px 2px 6px rgba(0, 0, 0, 0.2);
        }

        button {
            width: 100%;
            padding: 12px;
            font-size: 18px;
            background-color: #0056b3;
            color: #fff;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s ease, transform 0.3s ease;
        }

        button:hover {
            background-color: #003d82;
            transform: translateY(-2px);
            box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.2);
        }

        /* Suggestions Section */
        .suggestions {
            margin-top: 30px;
            border-top: 1px solid #ccc;
            padding-top: 20px;
        }

        .worker-card {
            border: 1px solid #0056b3;
            border-radius: 5px;
            padding: 10px;
            margin-bottom: 15px;
            background-color: #f9f9f9;
        }

        .worker-card h3 {
            color: #0056b3;
        }

        .contact-button {
            display: inline-block;
            margin-top: 10px;
            padding: 8px 15px;
            background-color: #28a745;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            text-decoration: none;
        }

        .contact-button:hover {
            background-color: #218838;
        }

        @media (max-width: 768px) {
            .container {
                padding: 10px;
            }

            h2 {
                font-size: 1.8rem;
            }
        }
    </style>
</head>
<body>
    <!-- Header Section -->
    <header>
        <div class="logo">
            <img src="data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBxMSEhUTExMVFRUVFhYXFRUVFRUYFxgVGRcXFhcWFxoYHSggGBolGxgXIjEiJSkrLi4uFx8zODMtNygtLisBCgoKDg0OGxAQGi0mHyUtLS8tLS0tLS0tLS0yLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLf/AABEIAJEBXAMBIgACEQEDEQH/xAAbAAACAgMBAAAAAAAAAAAAAAADBAUGAAECB//EAEcQAAIBAgQDBQUEBgoBAgcAAAECEQADBBIhMQVBUQYTImFxMoGRobEUQsHwIzNSYnLRBxUWc4KSssLh8TRToiQ1VHSUs9L/xAAaAQACAwEBAAAAAAAAAAAAAAABAgADBAUG/8QAMxEAAgIBAwMBBQcEAwEAAAAAAAECEQMSITEEE0FRBTJhcYEUIjOh0eHwYpGxwTRSciP/2gAMAwEAAhEDEQA/AL3bwq9fjRTYA5VpDRkFYdRtoVuIK4Fv1qTAnkK01kelNqBRFstaFSLYefOhthj0o1FktoTmuSlNGyKGyEbGh20TuNcizWKC2Gpo4hugrYxA6Ue3JE7kWJd1WCxT4ZTXQt1NUlySovgRWyaYspApkLWNFOpiOAq1CZJo9xaGGjlViYjRpbddC35UZQDtpXeo0Ip7FoSuYOaXfCxUygEVy6CipCuCIb7NWxYqRKCsAFHUDSIhKwpT/dA1ybVDUHSJZK2Fo7rQmopgaBsBQmUUVzQiaYUGy0JhRmobLRADrWQUPG4hLSNcuMFVdyfgPUzpFRP9p8NuHP8AlNAJMNZoLWqjf7U4fq3+X/muT2psfvf5R/OhYdiQZKCy0m3abD/v/wCUfzoT9o7H73wH86KkCh4rQ2FI/wBobP73wX+dHwHEbd/MEOqxmU6EA7HzFMpCOIRhQmFMslBZasTK2gBFDZaORQ2FMmVtCzrQStNMKCRTWJR7KMNXYw1bsY8GnUxCmuGqO67Eu4866Fvzp4lfKuSq+VEWxTu/SsyRTRsDkAffQ+5/dI99ElgWC+XwoTonl8aOcOOYNcNgVPM/GmQGK3LKkaH5g0pcsRyp98AOvzoD4WKdMRoQNs1JYOyCo5Gl+686kMFbAG4pmwR2B3MP0pV7RFS5QdR8RQbiDafnSUh7ZEMtDIFP3bIpdrQplH0Fc/UAFHWiq59a4NmsyGm3QLiwsj0rGFDCmuqmolGitclK6LVrOKNgpGgIrqtF65L01WLdGnFAcUUtXBFMkK2ANDZaYKVru6cQTZKGymn+7rhrdGwUUz+kJT9jP95b/wBVUq5hwFBDq22ihpGkyZAFXz+kZIwZ/vbX+qqdaWxlE3GDkDQLInxTsNfu/OklyFEflrRtyIIkedSeGsKSc5YDkQNxryIOu3zrd+zbAJDvOuVSg682B6eVAJFpaA2WPQV1lPSpS0ttv1jXc+mgjXpv+7EVmJsWwPAbhbSZAyzzg6H5VLIBOEtcr/IHW1cBnKCVgSNCSAZ1yk6CJc7IoBi7gDZh3J1gj76cjQjasgLPfTHj0SAfD7Pl7W8fd8677ImMW3nZb/WlRPcFouDrS7im2oTrV6KpMTYUFhTbJQ2WrEilsScUIinGWhm3TUVNnpaLRh6n413ZxQO5U+tN5kivNLIelcBLvWHM/OulxbDmfnRCVP34+Nc/Z2PssG+FWLII4naY88yaatY48oNJfZnHIfSuDaufsj3EVYpiOJLrj+REe6jG8pqHw7XBuJFPLe6qabULpGCimuGtL1P59a5Dr0rGWjqBpBvaB/6oDYYedNZK2EplIDiIjC/ma6GE8j8RTbsq6lgPU0BuIJ1J9xH1ptYug5GEHnWjhh1oZ4iCdo9TRO+U/k02pg0gGt/mK5K0d2XpXAAOoANMpC6QMVzlo5Xy+dcEetG0CmgLWqGbNHIrVFEsAbdc5KZmtEUyYrQqy1wTTLW6G1mnQjBiKIAK4NmuTZNNQtnZihPXL6bsB76Tv45R1Py+tLKUI8sDkVn+k1QcNbB2+0W59Ieqratou0fj8ane1/FO9axZZAB39h9WBLDOVK5TuNa9JxXZTCph84trIVWz5UysTyAj86VnyZb3juqA5M8k4hgrlnJ3ix3ltbqagzbecrabTGx1onA8NevXlt2Utu7K4AuAZYykk67GAfpV8bDW59hdAAPCNhsNtqJZspmEIu4+6PSsf2xXwVd5Pweb4jHO65cigRb1IBcZLaW/a6HJPviinh1wWBiTl7s3DaGvizBc+3SOdegLbT9lfgK6CL+yPgKH21f9Qd5eh5YtoswGgJIGpAAkwJ6CpPh2AbD8RuWXKlktMCUYspM2joSB16DnXrPZ/h9q4HLqXK5QEUwYJgtp0/DzFU3tJZVOKJbUyos3gp6+O0SPdqPdWvp5ubi62fxGva65NhawpTK262UrqJFTYiyUNrdPm3XBtUyQrZHtboZt1ItaoZtURWXNMeD90j/DRvta9Y9VoVi2eppv7O0bV4h5kmewkorkXzg7QfQGhi6Qedd3cMOYpd8OfP41dDKmBwTHVx/Wa19uqONk9TXaJFaFMpcB4YhuRrYxR50oAOYrsZRsKsUytwGVxNIcQ7Y4exbDvdBBnLBEEqQCM3sggkaEimQw6V5dgrfeFbJMr/Wt5YkwbajvnVtdRmVSJ/aPWrYJMqyXFF/T+kTh5AP2lQTy8WnloIoNvt3grtzu7eJZnJgKiXDMCdITXQH4VCY3gWFONw9rubWU2rxuLqJju1tyAdTM+utV3jvA8KvFLFhAEtsAHUbAlHbdiZnw8uYq2MIvy+DN3peT07BcRs32ZUuq7J7az41PRlOq+8U89heWlVLsbwq1h8RjEtrGU2iHMFiHSSpP8Qn31bg1K9mXx+8rFr1wIyrlZi0xEACI3k+fKq7hu0SLfsWHXx3EZ1yFmzM/igwuhjvDGsR6S/x/EOLqBWiLN9v1bPrCIIy6gy461Wb2It4u8mNw91i2HUpazW2UFlS8zjIVJYZQNQR7VOnYktnsSGM7cDu2Q2iHZLmiPqoBZAzFgAkgEgkx4W1kRT3BO1FkEWzdm2tnDKhKuX71iyEOAgILfowDsTtFUq1wj7Qmbu7d0Nn1F4LEswnLkgnTcmfOpxdBlfBuREad3cX4KxPyrJl62MJaUr9d0THGTVt/kXgcXskgBiSZIAR5IgH9noQffXRxtv8AbUHoWAPwOtedYPiVrD3Hd7Rt3CWPe3bdwAqSSJLrEgHLr+NSKdr7T+FHwk/uuoPwVhVi6yPmL/sHQ35Rc7eIViwUglDDRyMBo+DCuq89t9ozbvObSAs4UP3ZOWVJic+aTGkird2f4x9pzBkyFQCYMjWrcfVQk1H1A8cqsk63QsdjLVkZrjqg6swHw61V07aWGv8A6wi2LbeEIXLP3hWfCCQAqT5i4K06kUyajyy2UhxrilvDWzcuGBsBzZjsq9SaXPafC5M4uhpIVVAYMXJChACBrJA1qkdpcW1xDfux3jWSiWxqtkXu5aB1fumMt1bpFFz9CnLNRV2T/ZTtT9pLJo1yWZVy5ItAgDMSYYyY0+FS/GDeSzduAqCiMyqAzSwUkDlz5Qao2FxtrCLgnVpuW7dwXLYBlu98QTSTmDMdADUfxTtzevMEJCKWg5VDXFGohEbSdN5YgN18NV6rVc/4K4z2ryWqxxi0tm0b5LXnUEqC2r81S3b1f019aheJYx1Us7Jg0/eCnEMf3bc5UMcmJbyqr8NxWJ757K3lwwumGvXoW6FGykklkY7ZQRr0pjjnBbGFa0928MSx/Xl2YhdJyrlIMNJgzoU91NHCr+9+iHinQE8XwzXrKWLbOzX7GbEXjmuNFxToTsNNgF99e84vgqph82dyVVX1I7skxoo5b14viOP/AGlhas2VGHs4vDFGS3GVDcCqzsX3YnYL769JN98mUsxWdFJMCOg2FZeqlGLpq9ivK0uUc11baGB6EfWh1pq5lmQ2wgx00rQausUPG38TfU0Oi+SBM3T5VAY1M3ELHlYvn/3Wh+NTnKicN4cDcfExLW7bW06SxVmPr4V+Jq7p8nbyKXoaOmxPLkUF5Bi1Wd1TcDMRM6Az511kr0WPJqjbRZnwdubjdiJtVybNPm3XBSrdRRpEDarg2qfZKGUo6hdJauG4hJ1UGrAt+3HL00rzS1xmzuLo+DfypocbXbvOU7Nt8K8ZhyZenbUUmn6nqs3SLI7Ui0Y/EJOiio43B0qFucXtxmN0QecN/Kln7Q2Ru58ttfMa/Wkx4pydstjjjjVNliLL0rQy9KrNztNZjQlj0kAfGaHa7TrPsfC4p+oFa44JeojyQ9Sd4zjBZsXboEm2jNGp2E7D8+leaYftrjLpYkZFA+4m58mI/Guu1HbO5eZsLhly+2ruTJK7HYeEfGc0VTMThb1r9KGOh1ZZUiTE9CJ08ulbcWKKVTe74MHUZHNf/NlqxHaPGNaY9+yE6DK5Ee8Nv76q54veVhF1gRdu3MwJBzvlDMDO5gfzoDcUYxJnXYbTzNcq9sW2JXM5nKSNASY1PwrTGGk56lON6nYTE8Tu3TnZySCfGSZElmPmTJPPnQsFxNrbq6MhdYK5raaMDpDaMBHnUn2b4UL7OSMy2sqqp1BZidT1Agn3irM3AlMowLA6GZInloNFPSIPmDVWXrIY5aGjSsLkrAcH7cXRcZ2ZBcYgsbjEJdCKygKRAnx7N0XpIvXAe2trEWS5VhcWAbcDVidAhYwdCpM6QZ1FeKYux3Vy7ZYzkOUEnxftKBHPaffU/wBhuImzibeeRbLAm3PtuFcIwDESwLDXlAq2cIONoGObjKmWrthi72KBa2GtGwl1Xy3Q1t2JT9HntmJGWYYDkNJmvNRYvjUKwPUMoPyNeqdqO1Vu5bu2UKoWAJA8ZfqHKHKh0XmxI00rzfGXSLbRvGhnbXU+tSDcdjJ1OZrIlBp/yhrsrjLuHvhnzi2QQwzSOoMT+Zq+f2hsOfDiMsbiAPjnXSvJPtjftmnOEcTFpmdrS3SRENoB57Gs3V9Esr1+fhX+zRgy5Y7Sar6/qenY/jy2U777QWVZ8ClPGSIA8MRG/wAa8/4z2mvYgzcyqu4VUXMByljr8aVx+NN/Kq28qrmYKonUx02WQPiasXYPs0L4765zYxPIAkE+pIbXlA86qhhxdLDuZFv9P59S7W8r0oreC4xctnw3HHOPCVj+GBNeidlO0OIQLc+zi6l3MqunhJKSWHMFhB8MA6GJgmmP6pwWKR1tNny6MCGGvIieWm4ql8Nz4bEXsHn8D6EMVClsoe25BEZxpBBXWNRV2HLjzyf3akvXkrlHRG09vh/KLl2sxdvF2bd0PF5BBswZ1GZmloOURHnp1FVnDZkysrEgoWkLl8QGWBmnSZ35VaTbt3LVhIy3bZuqUOhHeObqskGHUElTz1mp9uxLdyCFkRy6bx6STV170jnZbc9SVnnuExj94112LgaqpA8Aa6mnXp8NtaY4k+W1duEqZxK20kSV7tLdtnGvQQJEafCRxPZ8hipdrZO8WyWMMDIgwB4QddaU43wAK8KLt3xZ3JyydZgFfDqWmeWvulN+BY6nu0Uu9BYubtwMIJdYZgd9pkRr028qk+Dd+7vbw9lpuGTctg97bXMcpVhBCzp7QBI12qcwfZVA+VlUg+JmdrrARBA8CrpM8jr5VJphe5QXLWcOQynurKKSmceEPOeC0trPLQb1a36I0x+7VIrfFuA4q9j7mEW+c0hizswT2AxuHLMOTJjzEmrV2/4ADhrCYZFPdP8Aqk7pUII1Zi5206nUjpNSrcIw7KpfEYxi2bQuACQivlbOWVRPhB5melK8C4ZgLhTPhbqs4uE95cDhAPDL5YgmTuARp5VLkWa5+Ev7kJf4PgMLYBsuGv3LuEzBriMy/p7TMgC6DUawPuirgTAAqC7aYLB2Fsrh7CktfsTeW4WyReQxBJMkT0qbOprn9byrMudva6+h3mrZ9aGzAb/SsS+oMxPkRp79daqx9JnyR1Qg2vgjPqV7sPjYzmDuAem4BoE0bG4rNE7wDIEHUTG+1Ld4PP5U8fZ/VtXLGwzlDVszsNU9wa3/APDk9WY+usfhUAZqwdn3mwB+yWn/ADE/QiqMbpnQ9m/i/T/aIj2L2XkRTbUrx3wtn6GoXgXHp75MQ4DW7zKpKkSm67TOn4V2ulzKUTX18NMtXqTt/EKgzMwUDckgD51EJ2owjP3YvpmO24H+YiPnUN27ujEWkSy4bx+OJ2gxpvvzHWvNmwBzFJ2YA+ExB1q95N9jDSZ7uGnWtGoLgPELVvD21uXlzga7n46b1lztVYBiLh8wo/E1Ypx9Ssqa4rM2VZ8hzjaYOpp4Y49596Iy7eXyqGRQBIQkmTAA1iCTTGs7EEw0Trl+Q3rz0saOzHO0O4bHEhkJOU7GPvcjvtST3mWQcx66E/CuGGVm32EEhjv6c/fXV65oWKtKaMVUka6SvUVFCmLLK2vkdSdT4oAnbb1kQBW1vEEeIiRpoPzNAuG4s+EAMdCDLZhMA9dPhRbbKIkNAgbHc6A6CBqTVmkzOZxh8Iq3HuT4nBDSDzMmB6rTWNuG6gtMwyBGVQFAOUiCPXQUocRJyqpYSTBkNEDpz1HuomIxarlLArOYiAc0AmZnoIPvouNtN8iPLJKrIxuzVvq+vn5fEVpuA24yl3gxp4uvSKnnK5c4hl5sYAiIEgDUQT8KEHB8WRQHOmpEidzGnn11qzuz9SmTsW4HOELm2095lzB1O6kxERG51qZbtDezB8toefdtqddYzdOdRgLKueArNoAw10J5zHpHI1oXXe5Cwc3QxA5784NVTxxnJykkwrLNKkyMxnCQ7tcZ2zOSzbAe7SQOXwoa8CRR7R6k+W+p51MlmJGUeDXUEnQciB+dK6xd8Bl7uG2EnTTKfET7oq9ZJVRVKUn5ELOFVAIVDI3ZA2nOSdq19nUz4LJ8u5X6UVbzGS5VddQGBkEElljUbc+powxFsQCQd+YOm4LH5RQtiboDbwVqVJt2I/uhry69aPjksEAW7VnTmbSxHkJ686E12GDANlY6ac+evSDz61u0jMxEAgQFjxRAn+c+lG3yDfyzrB3haV4t2fGsEi2AVPIgg/KmeEcWvYa13a92QczAspBBJJjwtEST8aTyMTDEqNJIPUZjvMgfhW2Az5Z25g+yBqfIbn4ClnGMlpkrXI0Jyg7i9xzhPF2sF2tW7XiJJjPB6CZ2BmkrgZ8S+JLAE7qZKgZRbiOfhrZIy7hRyXQjkdfpW0cjI24nUDWdOZ6TRhGMZOUVuwvLNrS3sWjhGPM5mY8lEs2u2irOp21mvRcF2qRlFtoEiBrPUD6V439sIOZZmIE8uU+WpNNrj3nKJBCqJmSSDOx2q2Lp2KpUeg8axLK1sho1PIER79RS3GJKzprvoOtVZeNOxzSzCYI0idvD8zU0eKgpJ08Ox32iKZtMZOxq85kMCNo+NKcVusttVDbE8/Mc6aw+KzhdB11GulZxVcyDTXpKj0qqSQ3gj8TiXNkANsOtLcFxLjMWc66bk0fEjKoBAJ8ttucevyoPCrDCAoJmAB1J+dLSF3shu0F55QFjHfWNCT/6ya61cFWo7tfgEs4UEgNda/h9f2B39swPPqfM1IIayZ2nVfH/AETqMUsdavO4PE8qDNbxJ1oU17X2THT0cF8/zbZy8nvMaxG1s9U+juPwoM0S8fBb/wAQ+DZv91LzW+PArHk1G1SfZu8O8e1zI7wDyEK31X41DYdqd7NAnG5h7K2Lik+bXLRUe/I3wrwHVYO11M8fhP8ALlHW6CT7sWv5sSnH8LKV5b2oJt3ZnwsoI33AykeugPvr2PiqyDXmXazB5rRYie7bNtPhOh+eU+gq3EtmjsdYteK/KKl9raJzfUVhxTCdfftPz6RQX1iDv0EnSuhgHaMpInqBPoKfbycY5bEMef5+Ncd83Jq4v2yGgmI3B/4G09K4YHr8m/CmIOYdrQ8GctIE/unnEVpMPcfTvVGsDXwwNNfM9Khb1i6oUhCQxOUpqTG4gCalOGcFvg5nYJOykgnzBiYMxp60soJb2bL2C3MC7MwN8LAAEftc58qLhg9sy14ZV08BJnWPdGp+NR2Lt3FDMQ4CmIMZgY36RPMUriUcEZ8wdhIQblSJn4TpUULVWLbsmcSjOhe3dDA6eLwxvM6mZP1o1jBtaK5rxVGgMF16kqDOmvl/Oq/ZxDWxkKkkmMpU/D11FbvG6uYOLiwJIIjKp9kkch60e2+AP4E9iEGhtuAIgkCdZMtvoZ9eXnQLGDvSoa7bIeQZMkKd5BieWmu9QJv3FRRDAHYwQGnXTkd6NYwuIuXGTKysvtZpERqBPWisdLkRpllQXQSlxgBBAAPmRqOc6dKVtjEOQMykO51bQpprnB94EE1FLhLzMhLAFlmSdhvBBjxRr76CcW65gxII1ggjN6g+VRY/kJRJjH33YjISySAVBA8MzqRHKncK2IOV3cKrkykwwI2B5EE1CPx65A8UbabiRtE7Ujc4mzyDv8Kbtt+CaX6FuLwrRcVSJyr1HIsdSTr9aXsWiFIc5kI0OYTmXYhhqAZPxqshXcjKGbQwQNwNT7hrTV7iDW/DrB6ny1+dDtehHFllUZfYCMxUyDEhSJKg85I28x50hi17tCTbR9VZmVtQwjwidY8WsaGovD8RDFsxKk/eGuvQDr/KgriWTMwcmDpoRII9ryqLG7FUXZZsPZdrkXZUALppDaCAAOhG3lQS17PEAIumdgB4CVX2dxJAPuNQC8Yc+LNLLET5dKOvFywYsdTGk6RzEdaHbkiOLLDbLnw5lADGD+1KlpidNwJ6zSwuuqhsoYMMzrAzAGTB6trynmKiFxCgS90jcgAa+W9ES8VYs1wAD7pBzTE+4+dTt0LRLk92kBJkBJgZmMSWM8+VBsX3XMipADDMg3JJjTlyG2lQ/wDWumupJzDTUdN+tG/rcqjFQZJEtrou8T6j6UdDDpZO4hsgl7QIIO3ijc5tJIj4UlaxxuPFtGBB384IGYnYSTvUcnG2Y6tA8qK/GH5CFOmblttMb/yo6GiaWhuxjFQhWRy7Awuoy6TmHXQEzUhb4193KwbNBka5dufnUJZ42UCtAMTEiSumUx0n8KdwnGgfFlBIWJjWOewnrSuL9ANFvwfHAAUBEAmOoGmnrqfhTj42FkkEzIPvn46fOqgZZhmEeGdj7OsCQDz5edOWLgyEhgx5wDz+QPp0opJoeLJJsV3hcKCG1JM+4iPzuasHZ9Vs94zA95lGUsQYU+1lA25ecGqxY4iqrmA1WAGywY32nWt4Tjj3HCoM7NIVRqSTyEVXOMpJpF2Cax5FJq68DHanimdVXU/pbWvT9Km9WVbRyhspynnBiekxFR3HcF3OEKsQ11mtZuYUC4hyg+REk+XlVvu8dtthskNJti3kgZAwA8Yb3T1rK4Rcacqq/qaPajeScZSWnbj6lVxB8RoU1lxvEfWuK950cNHT44+kV/g83Ldsaf8AVL5O4+K2/wDmg0Qa2T5XF+at/wDzS9XxAwguZZNW/s1ge7tgt7b+NvL9lfcPnNU1LDOygAnxLPoWG/zr0ewK8l7bjH7Smnu0r/nyO57Jx/dc39AePgiqVxNVJZGEhgQR1B0I+FWzHPvVG4lPeGuf083qZ2pxWjc8+4hgnt3WRlBVCQDtofEpAB3IIPvoacRYHbXlm00/DSn+39zu7tp+VxIP8SGJn0ZR7qql7iMnSZO/pyFae3fg4c8bUmhxsa5fKeXw8vWhvjzPjXXzGtJtjiZiZPTyrdnibKI0+VOofAGl+hZrF11AZgSkj9IvimRsCDv5VLngeaGt3mBOuV/a1J0nSedG74GwZ8CaZVAAjWQ2h08X0qIxvECilh6jbXXfeskrb+6Mtx3CYRxpcIuAzsraD2dQTp8KFxBwLgOXM2iqdCQDuNPdUae0DBZ3kydCNeU6686kcLxlXa2XAjczAb1U8vUa6nSppkt2gMkrOFX9GoCLrmltcrblpG5JJ+OtAs2XdnJAkHKCwGoG/ig8p8qDxbHI05SIg/eJJ8xNBfjaBjIIRjsoHtcyZ/O1KlJ7omzRw+XMMO6FgSDE5Yhic4b7o3186bx6Xlur/wCmZGdZgT4YeNRA51zcxwXKynYhuXlEASD/ACpNeN3J8BgFhBJ00iY67GnqT3SK7sY4liGtwrjWAUgSGnw+E+cx/wB1Gtw8YhHuZTICoDrAIOp9dRy0jU1MLxG1dZVcBsjZkgtmzADUsdFAM+ETMA8qlWxVtVOVRlA0UQFGsmQPX6UuuUKVbk43Km/C0GdbPtkqBpqEEc/vGZM+fkKNiuxklTnyD78wx5arrzk6manMLxNBcN2JYLG3KdZM/UUpxbjK3ArAxDEt1I0NMsuS6BqfgS7pcOS6IYC5TCwok8yx9qQAAI98iErTWZmDBcspaJzGdQBGgnQefOpPitxXwZyqWZcrgASczEA7SZgkT+FOYKxbTCrbY5XZfG4y5vEPZzjWNY01o66V+SeCvpw+1aC22Wc0OrHnOmbX022186PjOE2XsArC3c2bMZ8QY6yByjaemh3qW42tl8lzZEJ/RgKGcwAFBGwgD3UnjVN8eAw4K/ehVBgH1iTproKZTunYE3zYticBYNpVyrKyAV0bKxG55tOsnqaJwvs/bNwkajcIRpGo5jxDUQTrvTuCwSAkyO7BKZ3Ad3cDxEDTKoOkaH1qRt4hDMZM7rkJ0iBuSNwuuus+cxSubqkyW15IO1g7Cr3ZUSbubQbKCSACZMQd/IRE6c47h+e6odjaYCSxUeJADsGBj/ipfhGDt2nW6ToPCoYzqYOYRsSIOU7TvRxftPfe5MtlIXQQDyK6DXznnNL3HewCp4zszc1KMjqxMAwCAJKnwjntA5ke7jgvZu7cNxGHdlFDZjBABLAqw1E6bb/GrVev90FYa5ZJAJksRod9IHmY10pVuOgAACGZgSNDpoAJ67+nvp1mm1sMpuiv4Hgx7vu2WWuXB411KoATIJHhEj/3e6pPjHBe8tjLCRItrqF0JBDctTz361JY7iQVsykZhEj9onQTPSevKt4riiuEG0EMQJJIAI6+czvQeSbdgc3yVocDtoEFxmzkFmy7ZRMJH/R86PhwqqqhZzEKAs7QQT75OtS/EuEKXdmbKWXwQAOemY8wfQc6XwOCawReJkQAU8OZToSR1HpHp0Z5bV2HVfkNi8MoQkwxEAHQwCQYOmm1axmJF3w29ADPISYUGT08O2lAuYkNKGeu58R8q1wLg7i4O8uKQ06JnB8OpDSNI9em00qdK34F4CYOyFUEzOcFY1GkyWkb778hPWp/s7xdPtKuEAyhgCBqBlYEj4/nSq7ibYd1CXGyydwSY30AO519IqwW8HaTu3QEAKwbVQFmZZjoT5enoKE5Lz5HjPTJSXg77ScQd1ZlHgzWxm5Q1wLNeg3eO2Dhe7kybQQWsuiuPv5tt9etee8QxQt4UHN4Lb2GcgbhbqMxAG86mI516Tw/tlhc943eIYE2ywNgLfthguvtyRr7PvmmxY241F/Di/0NWfqZ9TLU6XjZfuefnEa+/wDGuxcr0LBdssAsh+IYZtvE2Iw/v9g01/bfh3/1+F//ACLf869HD2lp20/n+xhfRJ+fy/c89s62rnk1s/61/wB1A186vnEO2mEJt91xLBqA36TNft6rI0Gh5Zum41reL7aYAt4eI2AMv3cRZiZOusmaK9p/0fn+wv2H+r8v3Klwa/DrbKt4nVgw6rrB8tPmavNk6VGP2hwl51S1xC3fdtFti5aJ0EkgIAdgakbayK8117jLqXkiqct3ve/H+Ejt9DDRh0t8MRxYkmqfxdfHV2xYABAqmcX9o1V0/vGzJ7hTu2/Du+FgyQF70adT3cfSqy+FRWY213hNVmNtPUxNXniJDWuRyN9RH1j41BLhnZgVP6NQBAPhWQJJMyx8/L0nTKbTo4nUWpshMFwxc+ZeZggnbmYiknwV1iSCqCTAExHlA2qzYq2CrLbuZT0ga6bHTb4c6rgtX+ij+J0B+tNCTluUqTGcRxHKMgWFgGCWkjU7sZ/CuXuK1vR4PJS4YLHKQdKSvXCRLLlBnw8wN520rGVgo1aDrBafSn0lh2mHd1CiBrJkhR/3SuKF1NwY2MiQRyBjTrpXS4hiCFDQmrEAQBtqQNBrGtbtYhmGqsVGpy+W59KZIO4YYucomNpBJ9+tCx+LLED3AUozkDlr8qX7wggiQd+n0oqIVHyWnC8Tu2Uy92qGDDOZedJmRMR93Soy7iyWLyTMCZGvuAEbbUnZbMQWVROxGnlECu8SUG0SNhqfz8qVQSYulWSXDmGhD6yM0jb4GYp/C41Vf2iRG2ux+6OR9KhMJjPAR02iJPWZ1+FDuXWALASp0y7z6/8ANRwsVwbZP/agpOXRWkFeR32XlUVcumdjGaBPKTMHUwdqTGIPKdROp5jT8+tEXGQNQIPtDXXkDvExHwoKFBUKLa/FVtQEGUZeXMfifOo9uJs5J2BB5Dr56/DyqCxGLkiBr+HrQrd4lo8opFhQqg0iYw2LOciZHQ+fPTzod7FZXABO451Ed94wR93zpxLb3my2rRLQSYgHL18tI+NO4IOiia/rzMFUKGI0Aj3k69T1pA49kYgghzHlAJmT1/4rMR2Ye2md7izmgqJIA11LadBHqK5vxcUZGDMkQ06wDt50sYw8EaiP8PxzHRnMcxO8zp75/Cusbe1D5gNI1nbkZO0SdT1qNucUKpkQ+E79T0JjTaozE3WOWdBpC6R6nz9aKhuKsduyd/rYt7YzCObbjn7vnQcTxRmZdAIGkCBBgRJgxpUTbvAaESN/Oj2MICGd3gHUcz5TrTaIobQlyGxPEWJ0bUnxQBHXSt2OIEMCTpPuHOk7YSCCDBPhfnpy13+utCueGefQa6jr9aOlDaU9i3NxIsM5hpAgTy99DuYzMACxERMRG+refOoCzjQAFOmmh1id4O9DZ20MeEn0B+Wg0qvtFfbLDibr3JZZIUt4tNYkkb6mOnWmrHHwywFC6FQBEgbz7zv61CW+LaEaLGw1AEc53rjB4q02ZCNT4g4EGfz+RSvH6oGjY7+3tnIVtZIHkPU8/wDmrW3EhbtrMNMZuYA8vlvVSw2FEsc0NMqCBHPQief40viMWC4B3A8RWQJ05HnoflRcFJhcdT2LribqXLYAMplKESASp6AHqD8JqCvcBGZe7Zih9otklRMEnLsNRuBzqMXFysDNoZHl5zv/AN1rDY51jxEAzOTQwfaHnpTQi4rYMVJcEieDpOjvGo8ShTIJA6jXpNWLst2DtYyw13v7ilXKEAIdQqt0/eqs4LiSo6woAIgmAAD4o9dfrXoX9H3GoxPctot4CI2DqrEH3gEH0WqssslbM0dNNd1KfDKhxXsqMO7K9xyBqCAJjQfiKVwPA0uzFxojT2ZnoR61f/6SAqhnDZWSCCOsxHvmK8p/rN1nKQWzSrZdREER7+vSjilOceTR1uPtZlp4aTov/YDs4qYu3dLtNssVHhgkoymfcTXsCvFec9nrodbOJT2LkEgfdcaPbPoZFXt70CublyvXcmdRYo0tHDN41tKo/FHlj0qzYi6z6KD6naoDi+EA9lpPOKnT9RFT3GnibhRB2bQbMreywIPoaqHGsS9i41tiTB02AI5H3jX31ee7ZRIAPr/KofjnBlxhBZsjqCoZQCCCZGcHcA9CNzXShKM2cvqunbSvkpl3FZ+YUDcjc1j4+2dsx8/yKiMdZdGa22jKxUj94GD7qCpK6GQeYyg/Wr1BGDtokOKe03r/ALq4X9Tb9W+tZWU3gbwSuG/8C96r/wDtSuuBezf/ALof6xWVlV+H8xZEDb9ke78KXufd9/1rKyrkWIZwu59DQsR7XvrKygieRjhftH+EfWub/tr/AAfiaysoPkV+8zq77JoV3dfT+VbrKiAhziH6tf4V/GkLfP0rKyguAx4OF/Wf4vxr0vsd+suf3FZWVX1P4bK8vgiO1v6pP4rn1eqnht/j9DWVlTF7gYe6zeF9v4/jWcS9t/RfwrKyrVyMvf8AoBb8/OpHF+w3v/CsrKj5RJcoJwr2B6j8aSvbD+N/91ZWUq5Ej7zN4LY+q/WpS5+p/wAH+2srKkuST5IM7D3Uezv/AIP9y1uspmOx257S+n41GYn9Y3rWVlLHkXGGbY+76U3gPZufwn6isrKgfAK3t+fOrZ2P/wDLwn94f91ZWUmT3WSH4kfmixdvvvev4GvMeJ7p/d2/oaysqjpPdOj7T/5K/wDKPS/6L/8A5dc/+5b/AE2q9FucvSsrK5nV/iS+f6HQ6b8KPyA4j2G9Kr13l+eVZWVljyao8Cj7e4f6qRt8vf8AVqysrr9JyzD1fCPNe2f/AJd/+Jf9C1H4jcegrKyukcaXvH//2Q==" alt="BR Construction Logo">
            <h1>BR Construction</h1>
        </div>
    </header>

    <!-- Main Container -->
    <div class="container">
        <h2>Client Request Form</h2>
        <form id="clientRequestForm">
            <div class="input-container">
                <label for="clientName">Name:</label>
                <input type="text" id="clientName" placeholder="Enter your name" required>
            </div>
            <div class="input-container">
                <label for="clientEmail">Email:</label>
                <input type="email" id="clientEmail" placeholder="Enter your email" required>
            </div>
            <div class="input-container">
                <label for="clientPhone">Phone Number:</label>
                <input type="tel" id="clientPhone" placeholder="Enter your phone number" required>
            </div>
            <div class="input-container">
                <label for="workerType">Type of Worker Required:</label>
                <select id="workerType" required>
                    <option value="" disabled selected>Select Worker Type</option>
                    <option value="Painter">Painter</option>
                    <option value="Plumber">Plumber</option>
                    <option value="Carpenter">Carpenter</option>
                </select>
            </div>
            <div class="input-container">
                <label for="clientLocation">Location:</label>
                <input type="text" id="clientLocation" placeholder="Enter your location" required>
            </div>
            <div class="input-container">
                <label for="clientRequirements">Additional Requirements:</label>
                <textarea id="clientRequirements" placeholder="Describe any additional requirements" rows="4"></textarea>
            </div>
            <button type="submit">Find Workers</button>
        </form>

        <!-- Suggestions Section -->
        <div class="suggestions" id="suggestions" style="display:none;">
            <h2>Suggested Workers</h2>
            <div class="worker-card">
                <h3>John Doe - Painter</h3>
                <p>Location: City A</p>
                <p>Experience: 5 Years</p>
                <a href="contact.html" class="contact-button">Contact</a>
            </div>
            <div class="worker-card">
                <h3>Jane Smith - Carpenter</h3>
                <p>Location: City B</p>
                <p>Experience: 3 Years</p>
                <a href="contact.html" class="contact-button">Contact</a>
            </div>
            <!-- Add more worker suggestions here as needed -->
        </div>
    </div>

    <script>
        document.getElementById('clientRequestForm').addEventListener('submit', function(event) {
            event.preventDefault();
            const name = document.getElementById('clientName').value.trim();
            const email = document.getElementById('clientEmail').value.trim();
            const phone = document.getElementById('clientPhone').value.trim();
            const workerType = document.getElementById('workerType').value;
            const location = document.getElementById('clientLocation').value.trim();
            const requirements = document.getElementById('clientRequirements').value.trim();

            // Store client details in local storage (if needed)
            localStorage.setItem('clientName', name);
            localStorage.setItem('clientEmail', email);
            localStorage.setItem('clientPhone', phone);
            localStorage.setItem('workerType', workerType);
            localStorage.setItem('clientLocation', location);
            localStorage.setItem('clientRequirements', requirements);

            // Display suggestions based on worker type and location
            document.getElementById('suggestions').style.display = 'block';
            // You can replace this with a fetch call to your backend to get real suggestions
        });
    </script>
</body>
</html>
